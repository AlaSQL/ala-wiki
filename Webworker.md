# WebWorker

There are some different versions of webworkers for AlaSQL

### Option 1:
```html
    <script src="alasql-worker.js"></script>
   <script>
        alasql('SELECT VALUE 1+1', [], function(res){
            console.log(res);
        });
    </script>
```

Include file ```alasql-worker.js``` on the page, and it will download ```alasql.min.js``` as a webworker. After that alasql() function will post message to webworker, and then return result value back. The webworker version of alasql() is async.

Try this example [here](http://alasql.org/demo/012worker/).

If you want to load scripts into webworker you can use REQUIRE statement:
```sql
    alasql(['REQUIRE "script1.js", "script2.js" ']).then(function(){
        // sql can use script1.js
    });
```

Usually this required for user-defined functions, like:

```js
    alasql.fn.myfn = function(x){ return x*x; }
```

Please note that webworkers does not support localStorage so this is not supported for AlaSQL running in a webworker.


### Option 2:
```html
    <script src="alasql.js"></script>
   <script>
        alasql.worker();
        alasql(['SELECT VALUE 1+1'].then(function(res){
            console.log(res);
        });
    </script>
```

Include file ```alasql.js``` on the page, and then run alasql.worker(). It will create new Worker based on the alasql.min.js. After that you can use AlaSQL as shown before. Again, the webworker version of alasql() is async.

Try this example [here](http://alasql.org/demo/012worker/index2.html).

alasql.worker() function has three parameters:
```js
alasql.worker() - start worker
alasql.worker("alasql.min.js") - start worker from specified path
alasql.worker("alasql.min.js",["script1.js","script2.js"], callback) - load additional javascript files.
```

Try these three examples:
* [http://alasql.org/demo/012worker/index.html](http://alasql.org/demo/012worker/index.html) - option 1 - include alasql-worker.min.js, which loads alasql.min.js as webworker. AlaSQL catches messages
* [http://alasql.org/demo/012worker/index1.html](http://alasql.org/demo/012worker/index1.html) - option 2 - just load importScripts("alasql.min.js") inside webworker. AlaSQL does not catch messages
* [http://alasql.org/demo/012worker/index2.html](http://alasql.org/demo/012worker/index2.html) - option 3 - run alasql.worker() function, which loads alasql.min.js as webworker. AlaSQL catches messages

Your option is number 2. Can you check it?

***index1.html***
```html
    <h1>Worker demo: simple worker</h1>
    <p>See Console for worker results</p>
    <script>
        var worker = new Worker('other-worker.js');
    </script>
```
***other-worker.js***
```js
    importScripts('../../console/alasql.min.js');
    if(alasql) {
        console.log('AlaSQL is here?',alasql('SELECT VALUE TRUE'));
        console.log('self.onmessage is free?',!self.onmessage);
    }
```;

