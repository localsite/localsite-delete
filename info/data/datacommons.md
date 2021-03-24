# Install DataCommons.org Tools

Clone the [DataCommons tools fork](https://github.com/modelearth/tools) to experiment on your local computer, or clone directly from [datacommonsorg/tools](https://github.com/datacommonsorg/tools)  

You may need to [update node.js](https://nodejs.org/en/download/current/) if you are older than 10.0.0. Run to check:

	node -v  

<!-- node install says: Make sure that /usr/local/bin is in your $PATH. -->

Control \` to open terminal.    

	cd covid19-dashboard

To prevent initial error:  

<!--
In package.json AND package-lock.json, change eslint from ^6.6.0 to:

	"eslint": "^7.13.0"
-->

Fix the dependency tree, follow these steps in the exact order. (Skip step 1 if you don't have a .lock file yet. Also skip step 2 if you don't have a node_modules folder yet.):

  1. Delete package-lock.json (not package.json!) in your project folder.
  2. Delete node_modules in your project folder.
  3. Remove "eslint" from dependencies and/or devDependencies in the package.json file in your project folder.
  4. Run npm install, depending on the package manager you use.


<!-- 

Wasn't need, was using VSCode

Optional, Run the following within your local **tools/covid19-dashboard** folder.  

Setup the environment:

	python3 -m venv .env

Run one of these:

OSX / Linux:

	source .env/bin/activate

Windows:

	\.env\Scripts\activate.bat

Optional, upgrade pip and postgresql

	pip install --upgrade pip

Install dependencies

	pip install -r requirements.txt

-->

Install dependencies (generates node_modules folder)

	npm install

If prompted, run:

	npm audit fix --force


Note: The dashboar.yaml file contains handlers for a build folder. How do we execute it? The .eslintignore file also omits build/  
<!--
Build the app - this will created the index.js file

	npm run build 
-->


Launch site. Allow up to 30 minutes. A browser will automatically launch at http://localhost:3000/  

	npm start




You'll briefly see the DataCommons.org header when refreshing, then an error with the babel dependency occurs.

<!--
Chaning to the following did not allow browser to launch  

    "@babel/eslint-parser": "^7.13.0",
    "@babel/eslint-plugin": "^7.13.0",

-->
