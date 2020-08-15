# spase-model-search

A browser based tool to search and explorer an information model.

# Getting stated

1. Clone this repo.
2. Place the contents of the "pages" folder in the desired location of your web site.
3. Update "config.js" to match where JSON versions of the model specification are stored and the list of versions available.
4. Access the "index.html" in the pages folder.

# Configuration

There are two configuration files that are used by the model search page. One is a general configuration file called "config.js" 
and the other is a model version file which can have any name. The name of the model version is set in the general configuration files.

## config.js

The file "config.js" co-located with the data model search web page has the contents:

```
var config = {
	modelVersion: "2.3.1",
    modelName: "Base Model",
    modelVersionFile: "modelVersions.json",
    modelFolder: "model",
	modelPrefix: "spase",
}
```

where

**modelVersion**: The default version of the model to display.

**modelName**: The name of the model to display in the search web page.

**modelVersionFile**: The name of the file containing version information. The file name can contain path information and must be relative to the location of the search web page on the web server.

** modelFolder**: The name of the folder containing model specification JSON files. The file name can contain path information and must be relative to the location of the search web page on the web server.

**modelPrefix**: The prefix for model specification JSON file names. When loading a file the prefix is followed by a dash (-) then the version number and a ".json" prefix.

## modelVersions.json

The model version file contains a list of available model specifications. The format is:

```
{
	"release": [
		{"version": "1.0.0", "released": "2020-01-02" },
		{"version": "2.0.0", "released": "2020-02-03" },
	],
	"current": {"version": "2.0.0", "released": "2020-02-03" },
	"draft": ""
}
```
When the search page is first loaded the "current" version will be selected and displayed.

# Testing

Testing the search tool in development can be aided by running a Docker container attached to the soure files. 
There are scripts in the "docker" folder to aid in testing during development. 
Use **docker-up** to launch a web server in a Docker container that is attached to the "pages" folder and 
use **docker-down** to stop and remove the docker container. 

Because of differences on how paths are handled in Windows 10 and Linux systems there are both Windows batch scripts and Linux Bash scripts.
Use the appropriate script for your operating system.

On Linux
```
bash docker-up.sh
```

On Windows 10
```
docker-up.bat
```
 
# Template files

The dictionary entry formatting (entry.hbs) and the tree item formatting (tree.hbs) is specified in <a href="https://handlebarsjs.com/guide/">Handlebars</a> language.
These files are loaded dynamically by the search page.
