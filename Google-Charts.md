# Google Charts and AlaSQL

AlaSQL can be used to load and prepare data for Google Charts.

Based on [StackOverflow.com question](http://stackoverflow.com/questions/28999581/alasql-and-google-charts/29010186#29010186)

### Question

The plan is to use alaSQL to extract data from an excel spread sheet and use the resultant array as the source for a Google chart. How I can do it?

### Answer

```js
    <script src="alasql.min.js"></script>
    <script src="xlsx.core.min.js"></script>
    <script type="text/javascript" src="https://www.google.com/jsapi"></script>
    <div id="chart_div_cities"></div>
    <script>
        google.load('visualization', '1', {'packages':['corechart']});
        google.setOnLoadCallback(drawChart);

        function drawChart() {
            var data_cities = [];
            data_cities = new google.visualization.DataTable();
            data_cities.addColumn('string', 'City');
            data_cities.addColumn('number', 'Population');
            data_cities.addRows(3);
            var row_Counter = 0;

            alasql(['SELECT * FROM XLSX("cities.xlsx", {sheetid:"Cities", range:"A1:B4"})']).then(function(res){
            	var xlData = res[0];
                var items = [];
                xlData.forEach(function (key, val) {
                    data_cities.setCell(row_Counter, 0, val.City);
                    data_cities.setCell(row_Counter, 1, val.Population);
                    row_Counter = row_Counter + 1;
                });

                var chart_cities = new google.visualization.ColumnChart(
                     document.getElementById('chart_div_cities'));

                var options_cities = {
                  'title': 'Populations of Major Cities',
                  'width': 1800,
                  'height': 400,
                  vAxis: { title: "Population", titleTextStyle: { fontSize: 16, bold: true, italic: false } },
                  hAxis: { title: "City", titleTextStyle: { fontSize: 16, bold: true, italic: false } },
                  seriesType: "bars",
                  animation: {
                      duration: 800,
                      easing: 'inout',
                  },
                  allowHtml: true,
                  bar: { groupWidth: "65%" },
                  legend: { position: "bottom" },
                  is3D: true,
              };

              chart_cities.draw(data_cities, options_cities);
           });
        };
    </script>

```

please fine `xlsx` at https://cdnjs.com/libraries/xlsx