# AsTeRICS based AT solution

This folder contains an AsTeRICS based solution using the [APE (AsTeRICS Packaging Environment)](https://github.com/asterics/AsTeRICS/wiki/AsTeRICS-Packaging-Environment-(APE)) template folder structure.

# Prerequisites

Please follow the instructions of this [tutorial](https://github.com/asterics/AsTeRICS/wiki/AsTeRICS-Solution-Template-Repository#prerequisites)

# Demos / Examples

You can try some (other) [demos](http://asterics.github.io/AsTeRICS/demos.html) and [asterics solution example repositories](https://github.com/asterics?utf8=%E2%9C%93&q=topic%3Aexample&type=&language=) here.

# Run project

Enter

```ant run```

to build all the dependencies and start the ARE.

You can also start the ARE using the ARE start-scripts in the ```build/merged/bin/ARE``` folder.

# Folder structure
Subsequently you can see the simplified folder structure of an APE-based project, which contains an ant build file (**```build.xml```**), a property-based configuration file (**```APE.properties```**), the **```custom/bin/ARE```** folder to store the solution-specific files (e.g. model files), a **```build```** folder and a **```package```** folder for native installer customization. 

```
build
  |- merged
  |- deploy
custom
  |- bin/ARE
    |- data
    |- images
    |- LICENSE
    |- models
      |- <custom model file>.acs
      |- ...
    |-profile
    |- web
      |- webapps
        |- startpage
          |- start.html
        |- <your webapps folder>
          |- index.html
package
  |- linux
  |- windows
  |- macosx
APE.properties
build.xml
```

# How to use the repository

First, please read the tutorial about the [**AsTeRICS Solution Template Repository**](https://github.com/asterics/AsTeRICS/wiki/AsTeRICS-Solution-Template-Repository).

## Quick howto
Put all your custom files (model files, images, config files,...) to the [custom/bin/ARE](custom/bin/ARE) folder. 

In case you have a web UI put the files (.html, images, .css, .js,...) to the document root [(custom/bin/ARE/web)](custom/bin/ARE/web) of the built-in webserver. The webserver also provides a [websocket](https://github.com/asterics/AsTeRICS/wiki/AsTeRICS-Websocket). Finally the ARE provides a [REST API](https://github.com/asterics/AsTeRICS/wiki/AsTeRICS-REST-API) that can be used within a web application.

Before the project can be run it must be [built](#build-project) (builds the AsTeRICS repository and copies/merges needed plugin jars and project files to the ```build/merged/bin/ARE``` folder). You can also directly [run](#run-project) the ARE with the project's solution.

# Recommended workflow

1. Save custom files (models, images, config files,...) to the custom/bin/ARE folder or subfolders (e.g. web/...) or modify them
2. Call ```ant APE-copy & ant run-quick```
3. This should automatically open [http://localhost:8081](http://localhost:8081) in your standard browser.
4. If you want to modify the running model, press 'F8' to open it in the WebACS, then modify and upload it. To save successful modifications permanently, save the model file to the ```custom/bin/ARE/models``` folder again.
5. Kill program and go to step 1

# Release project

To create a native installer open a console and run

```ant deploy```

Please also check additional [dependencies](https://github.com/asterics/AsTeRICS/tree/master/bin/APE#dependencies) and [usage examples](https://github.com/asterics/AsTeRICS/tree/master/bin/APE#example-usages-of-the-build-infrastructure). 

# Other ant targets

To see all supported targets, call

```ant -projecthelp```

# Changing AsTeRICS snapshot (ARE) used

The property ```ARE.baseURI``` defines the location of the ARE used for the execution of the project. 

APE automatically searches for an ARE at the following locations:
1. ```dependencies/AsTeRICS/bin/ARE``` (if Asterics is added as submodule)
2. ```../AsTeRICS/bin/ARE``` (if it's an APE projectdir withouth FABI and FLipMouse folder structure)
3. ```../../AsTeRICS/bin/ARE``` (if it's an AT solution folder structure)
4. ```C:/Program Files (x86)/AsTeRICS/ARE/``` (if there is an Asterics installation on windows)

You can also set ARE.baseURI manually, either in the file ```APE.properties``` or within an ant call, e.g. 

```ant -DARE.baseURI=<path to ARE> run```
  
```ant -DARE.baseURI=D:/AsTeRICS/AsTeRICS/bin/ARE/ run```
 
# License

Dual license MIT or GPLv3 with CLASSPATH exception. Please read more in the [license section](https://github.com/asterics/AsTeRICS/wiki/Licensing) of the wiki.
