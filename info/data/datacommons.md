# Install DataCommons.org Tools

Clone the [DataCommons tools fork](https://github.com/modelearth/tools) to experiment on your local computer, or clone directly from [datacommonsorg/tools](https://github.com/datacommonsorg/tools)  

You may need to [update node.js](https://nodejs.org/en/download/current/) if you are older than 10.0.0. Run to check:

	node -v  

<!-- node install says: Make sure that /usr/local/bin is in your $PATH. -->

Control \` to open terminal in VS Code.    

	cd covid19-dashboard


Run

	gcloud auth application-default login

Add a quota project (haven't tried yet)  

	gcloud auth application-default set-quota-project

Choose your Google account <!-- map.g 00 --> and you should be directed to a page saying "You are now authenticated with the Google Cloud SDK!"  

<!--
Note, the step above does not fix the "Failed to compile" errow below.  Maybe we need to make additional Google Cloud settings, perhaps for a specific project?  
GCP Project datcom-tools-staging is mentioned on the readme.  


To prevent initial error:  

In package.json AND package-lock.json, change eslint from ^6.6.0 to:

	"eslint": "^7.13.0"
-->

<!--
Fix the dependency tree, follow these steps in the exact order. (Skip step 1 if you don't have a .lock file yet. Also skip step 2 if you don't have a node_modules folder yet.):

  1. Delete package-lock.json (not package.json!) in your project folder.
  2. Delete node_modules in your project folder.
  3. Remove "eslint" from dependencies and/or devDependencies in the package.json file in your project folder.
  4. Run npm install, depending on the package manager you use.
-->

## Create a Virtual Environment (optional)

Optional, run the following within your local **tools/covid19-dashboard** folder.  
Wasn't needed, specifically when using VSCode, you can skip to "Install and Start" below.  

Setup the environment:

	python3 -m venv .env

Run one of these:

OSX / Linux:

	source .env/bin/activate

Windows:

	\.env\Scripts\activate.bat

Optional, upgrade pip  

	pip install --upgrade pip

Install dependencies

	pip install -r requirements.txt


## Install and Start

Run:
<!-- You’d need to have the google cloud sdk installed, as well as app engine (via “gcloud components install app-engine-python”). Maybe already had those. -->

	./run_locally.sh

Open new terminal  

<!--
Carolyn Au says this should no longer be necessary  

	npm audit fix --force
-->

Install dependencies (generates node_modules folder)

	npm install


<!--
Note: The dashboar.yaml file contains handlers for a build folder. How do we execute it? The .eslintignore file also omits build/  

Build the app (You can skip this step. npm start does the same and also launches a browser.)

	npm run build 

-->

Launch site. A browser will automatically launch at http://localhost:3000/  
<!--Launches in a minute. One time when we had an error, it took abiout 20 minutes.-->

	npm start


<!--
You'll briefly see the DataCommons.org header when refreshing, then a "Failed to compile" occurs with a long list starting with the following:  

	src/App.tsx
	  Line 25:9:    Replace `GeoIdToDataType,·GeoIdToPlaceInfoType,·KeyToTimeSeriesType` with `⏎··GeoIdToDataType,⏎··GeoIdToPlaceInfoType,⏎··KeyToTimeSeriesType,⏎`                    prettier/prettier
	  Line 38:3:    Delete `⏎`                                                                                                                                                         prettier/prettier
	  Line 66:27:   The 'URLSearchParams' is not supported until Node.js 10.0.0. The configured version range is '>=8.0.0'                                                             node/no-unsupported-features/node-builtins


Chaning to the following did not allow browser to launch  

    "@babel/eslint-parser": "^7.13.0",
    "@babel/eslint-plugin": "^7.13.0",

-->

The site header should be visible.  
We're currently figuring out how to pull the data from Google Cloud.  

