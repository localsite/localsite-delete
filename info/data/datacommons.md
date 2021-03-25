# Install DataCommons.org Tools

Clone the [DataCommons tools fork](https://github.com/modelearth/tools) to experiment on your local computer, or clone directly from [datacommonsorg/tools](https://github.com/datacommonsorg/tools)  

You may need to [update node.js](https://nodejs.org/en/download/current/) if you are older than 10.0.0. Run to check:

	node -v  

<!-- node install says: Make sure that /usr/local/bin is in your $PATH. -->

Open terminal. (Type control \` if you're using VS Code.)  

	cd covid19-dashboard


Run the following and choose your Google account <!-- map.g 00 -->. You should be directed to a page saying "You are now authenticated with the Google Cloud SDK!"  

	gcloud auth application-default login

See if you are logged in  

	gcloud auth list

You may neet to run  

	gcloud auth login 'your_email@domain.com'

If that does not work, this will open a browser window (delete this after confirming above works)

	gcloud auth login `ACCOUNT`

Add a quota project (haven't tried yet)  

	gcloud auth application-default set-quota-project QUOTA_PROJECT_ID [optional flags]


Returned:  

API [cloudresourcemanager.googleapis.com] not enabled on project 
[404342046192]. Would you like to enable and retry (this will take a 
few minutes)? (y/N)?

Use the resulting link to enable the Service Usage API.  


[Steps](https://cloud.google.com/resource-manager/docs/creating-managing-projects) for creating a project and getting your QUOTA\_PROJECT\_ID  

Might not be needed:  
Go to [Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts?authuser=1) and click "Create Service Account"  

Assuming: The QUOTA\_PROJECT\_ID is the ID that appears after the project name in the [GCP Dashboard](https://console.cloud.google.com/home/dashboard)  
<!--
	Note: Georgia Directory is listed under Resouces Pending Deletion
-->

To get info about set-quota-project:  

	gcloud auth application-default set-quota-project --help

Control-C returns you to terminal. To view addition gcloud commands:

	 gcloud help

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
Wasn't needed. You can skip to "Install and Start" below.  

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

You need to have the google cloud sdk installed and the app engine.  To confirm you have app-engine-python installed, run the following (If needed, install by running “gcloud components install app-engine-python”). Update to the latest Cloud SDK by running "gcloud components update" (also updates other components and adds )  

	gcloud components list

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
-->

Launch site. A browser will automatically launch at http://localhost:3000/  
<!--Launches in a minute. One time when we had an error, it took abiout 20 minutes.-->

	npm start

Note that the development build is not optimized.
To create a production build, use: 

	npm run build.

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
We're currently figuring out how to pull the data from Google Cloud using a QUOTA_PROJECT_ID.  

## Also See

[Contributing Data]()  
[Developer Guide](https://github.com/datacommonsorg/website/blob/master/docs/developer_guide.md)  