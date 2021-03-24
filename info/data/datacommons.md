# Install DataCommons.org Tools

Clone the [DataCommons tools fork](https://github.com/modelearth/tools) to experiment on your local computer, or clone directly from [datacommonsorg/tools](https://github.com/datacommonsorg/tools)  

We're still testing the following...  

You may need to update node.js.  Download here: https://nodejs.org/en/download/current/
<!-- node install says: Make sure that /usr/local/bin is in your $PATH. -->

Run the following within your local tools/covid19-dashboard folder.  

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

Install dependencies (generates node_modules folder)

	npm install

If prompted, run:

	npm audit fix --force

<!--
Build the app - this will created the index.js file

	npm run build 
-->

In package.json and package-lock.json, change to:

	"eslint": "^7.13.0"
    "@babel/eslint-parser": "^7.13.0",
    "@babel/eslint-plugin": "^7.13.0",

Launch site

	npm start
