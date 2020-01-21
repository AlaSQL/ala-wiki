#!/bin/sh
: '
# How to release a new version of AlaSQL

AlaSQL uses [git flow](http://danielkummer.github.io/git-flow-cheatsheet/) to manage development and [Semantic Versioning](http://semver.org) to manage versioning. 
**In practice the result is that the master branch is never updated without updating the version number.**
That includes changes like corrections to documentation files such as README.md. 

The formatting of this document is a bit funny because it works both as a markdown document and a `sh` script. Running the command
```sh
> npm run release
```
will `curl` the content of this wiki page to `sh`.

----

'
go(){

#Please update the following checklist where you see a better way...


#### # Get latest version of master and develop 
    run "Make sure you have the last version of both master and develop" "git checkout master && git pull && git checkout develop && git pull"

    
#### # Install node modules
    run "Install node modules" "yarn install"

    
#### # Check for node modules to be updated
    run "Make sure all node modules are up to date" "yarn uptodate"





#### # Verify that `yarn test` does not give any errors
    echo "For the checklist to continue build+test must be OK" && hitkey
    yarn test || exit 1
    hitkey && br



#### # What kind of changes are involved in this release
commitUrl="https://github.com/agershun/alasql/commits/develop"

roadmapUrl="https://trello.com/b/qxz65pVi/alasql-roadmap"

    run "Identify next version number.${CR}First, determine if the changes involved are:${CR}Bug fixes, Added functinality or Incompatible API changes" 'open $commitUrl 2>/dev/null || { echo "No browser found to open: $commitUrl" && hitkey ; }'


#### # Pick the correct version number: 
    preVersion=`npm list alasql --silent --depth=0 | grep -o "alasql@[^ ]*" | cut -c8-` # Dancing around as npm view .. version will give info about any globally installed package before the local one
    while true; do
    	echo "\033[0;32mVersion is now $preVersion" 
    	echo "For the format X.Y.Z select part to bump:" 
    	echo "  X) MAJOR - incompatible API changes" 
    	echo "  Y) MINOR - added functionality in a backwards-compatible manner"
    	echo "  Z) PATCH - backwards-compatible bug fixes\033[0m"
    	echo "  Q)         Do not bump the version"
    	read -p ": " v
    	case $v in
    		[Xx]* ) ./node_modules/.bin/mversion major ; break ;;
    		[Yy]* ) ./node_modules/.bin/mversion minor ; break ;;
    		[Zz]* ) ./node_modules/.bin/mversion patch ; break ;;
    		[Qq]* ) echo "No changes made" ; break ;;
    		* ) echo "Please answer X, Y, Z or Q" && echo ;;
    	esac
    done
    hitkey
    br	
	

##### #  identify new version
    thisVersion=`npm list alasql --silent --depth=0 | grep -o "alasql@[^ ]*" | cut -c8-` # Dancing around as 'npm view .. version' will give info about any globally installed package before the local one
    echo "Version was bumped: $preVersion -> $thisVersion"
   


#### # Switch to or create a release branch `git flow release start x.y.z` (in source tree click "git flow" at the top right). Name it exactly as the new version number (for example "0.2.0"). 
    
     if grep -m 1 -q 'release/' <<< "`git branch`"  ; then
         git stash --quiet && git checkout -q "release/$thisVersion" 2> /dev/null && git stash pop --quiet || echo "Problem switching to branch release/$thisVersion${CR}but there is a branch named `git branch | grep -m 1 -o 'release/.*'`" && git stash pop --quiet && flee "Please delete the `git branch | grep -m 1 -o 'release/.*'` branch or rerun this checklist ${CR}making sure the version bump matches the existing branch version" ;
     else
         run "Create and switch to a new release branch" "git stash --quiet; git flow release start $thisVersion ; git stash pop --quiet"
    fi


   
#### # Update CHANGELOG.md with some words to what has changed. Select a city name the flavor of the day as part of the title. You can see [the commits](https://github.com/agershun/alasql/commits/develop) and [the roadmap](https://trello.com/b/qxz65pVi/alasql-roadmap) for inspiration to what to write
    run "Update CHANGELOG.md with some words to what has changed.${CR}${CR}Set title as '$thisVersion \"CITYNAME\" (DD.MM.YYYY)'${CR}For example '$thisVersion \"Athens\" (13.07.2015)'${CR}${CR}Select a city name (flavor of the day) as part of the title." '{ open $commitUrl 2>/dev/null || echo "No browser found to open: $commitUrl" ; } && { open $roadmapUrl 2>/dev/null || echo "No browser found to open: $roadmapUrl" && hitkey ; } && { open CHANGELOG.md || vim CHANGELOG.md ; } && echo "Please edit CHANGELOG.md before continuing"'




#### # Copy al content from https://github.com/agershun/alasql/wiki/readme into README.md
    run "Update README.md with the one on the wiki" "curl https://raw.githubusercontent.com/wiki/agershun/alasql/readme.md -o README.md"



#### # Verify that `npm test` does not give any errors
    echo "For the checklist to continue build+test must be OK and a test cover report will be created" && hitkey
    yarn test || exit 1
    yarn test-cover 
    hitkey
    br

#### # push package to npm `npm publish` 
    run "push package to npm" "npm publish"


#### # Add and commit changes
    run "Add and commit changed files" "git commit -am 'Updated version in files to $thisVersion'"


#### # Finish release `git flow release finish x.y.z` (for source tree just clicking "git-flow" at the top right corner)
    run "Finish git-flow release" "git flow release finish $thisVersion"


#### # Push develop, master and tags to github 
    run "Push develop and master + tags to github" "git checkout master && git push && git checkout develop && git push && git push --tags"

#### # [Create a new github release](https://github.com/agershun/alasql/releases/new) Same description as CHANGELOG.md and with release title as `"CITYNAME" (TODAY)` for example `"Athens" (19.01.2038)` You should be able to find it in the dropdown in "Tag version" - and select **master** as branch.
releaseUrl="https://github.com/agershun/alasql/releases/new"

    run "Create a new github release.${CR}${CR}Same title and description as in CHANGELOG.md but without title version number${CR}${CR}You should be able to find $thisVersion in the dropdown \"Tag version\"${CR}${CR}Please select MASTER as branch(!)${CR}" '{ open CHANGELOG.md || vim CHANGELOG.md ; } & { open $releaseUrl 2>/dev/null || echo "No browser found to open: $releaseUrl" && hitkey ; }'


###### You are done !
    allOK
}

# Things to check before you run the checklist
	check(){
	clear && echo
	echo "How to release a new version of AlaSQL" && hr 
	info "Checking all is OK to start the checklist..." && echo 

#### # Check npm is installed
	node -v > /dev/null 2>&1 || flee "Please install npm before continuing"  

#### # Check npm is installed
	yarn -v > /dev/null 2>&1 || flee "Please install npm before continuing"  

#### # Check we are in same folder as package.json
      [ -f ./package.json ] || flee "Please cd to package root folder" 

#### # Check we are in the AlaSQL module
      [ "alasql" = "$(npm view .. name)" ] || flee "This checklist is ment for AlaSQL" 


#### # Check git is installed
      git version > /dev/null 2>&1 || flee "Please install git before continuing"  


#### # Check git-flow is installed
      git flow version > /dev/null 2>&1 || flee "Please install git-flow before continuing" 


#### # Check repo has git-flow config
      grep -q 'gitflow' ./.git/config || run "To run the checklist you must prepare the repo for git-flow${CR}Its recommended to accept the suggested values" "git flow init" || flee "Please 'git flow init' before restarting this checklist"


###### Now go do the steps in the checklist
      go
    }


# Functions to make it all easy

    pause() {
     OLDCONFIG=`stty -g`
     stty -icanon -echo min 1 time 0
     dd count=1 2>/dev/null
     stty $OLDCONFIG
    }

    todo(){
      echo "$(echo "\033[0;101mManual action:\033[0m \033[0;32m$1\033[0m ")" 
      if [ -n "$2" ]; then
        echo "This might help you: \033[1;36m$2\033[0m"
      fi
      info "Hit a key when its done..." 
      pause
      br
    }

    CR=`echo '\n.'` ###### Get a carriage return into `CR`
    CR=${CR%.}

    hr () {
        echo "‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗‗" && echo
    }

    br () {
      clear && hr
    }
	
    run () { ###### Aks if user wants to execute something
        while true; do
            read -p "$(echo "\033[0;32m$1\033[0m")${CR}Would you like to execute: $CR$(echo "\033[1;30m$2\033[0m")$CR(Yes) " yn
            case ${yn:-Y} in
                [Yy]* ) { { eval $2 && hitkey } || flee "Please solve the problem manually and restart this checklist"; } ; } && br && return;;
                [Nn]* ) echo "$(echo "\033[0;101mThis step was skipped - Please fix manually...\033[0m")" && hitkey && br && return 1;;
                [Qq]* ) echo "Are you a quitter?" && exit;;
                * ) echo "${CR}Please answer $(echo "\033[0;32mY\033[0mes or \033[0;31mN\033[0mo")";;
            esac
        done
    }
    info () {
        echo "\033[1;30m$1\033[0m"
    }
    hitkey () { 
         info "Hit a key to continue..." && pause 
    } 
    alert(){
      echo "\033[0;101m$1\033[0m"
    }
    flee(){
      echo && alert "$1" && echo && exit 1
    }
	  allOK(){
      br
      echo "\033[0;32mAll Done!\033[0m${CR}"
	}
    check