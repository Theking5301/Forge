# Forge Template
[![Build Status](http://galaxy.nctu.me:8080/buildStatus/icon?job=Examples%2FForge%2Fmaster)](http://galaxy.nctu.me:8080/job/Examples/job/Forge/job/master/)

This is a Forge mod template using Jenkins CI/CD. By clicking the [**Use this template**](https://github.com/jenkins-example/Forge/generate) Button,
 you can easily create a new Forge project based on our default setup.
 
## Getting Started
> This readme mainly covers the IntelliJ IDEA setup.
> If you using another IDE, please refer to our [Wiki](https://github.com/jenkins-example/Forge/wiki) page.
 
To get started, simply click the [**Use this template**](https://github.com/jenkins-example/Forge/generate) Button (or this link:sunglasses:) to create a new project for your Github account or organization.
If you don't want to create project in Github, make it ease to clone the project to your local storage.
 
## Import project using IntelliJ IDEA
> In this guide, we use IntelliJ IDEA 2019.1 version, but it should work on older version and future updates.
 
1. If you have created template from Github, you need to clone it to your local repository.
2. Open your IntelliJ IDEA and land on the home page. If you have opened a project before, just close the current project and you will see the home page.
3. Click the **Import project** button, and select the **build.gradle** file in the root root directory of this template, and then click Import, this action will take about a few minutes.
4. After IDEA importing your project, you can open the Gradle panel in the right and click the *Reimport All Gradle Projects* to let the IDEA rerun the sync task and thus suppress the warning shown by code analysis tool.
5. Then, expand the *tasks/forgegradle* folder in the Gradle panel, and click the **setupDecompWorkspace** to run it. It will take some time because the forgegradle plugin is decompiling minecraft into source that you can look up when developing mod.
6. Click **getIntelliJRuns** to let forgegradle configure your development environment.
7. After that, you will see 2 new configurations set up by forgegradle, but those 2 configurations need additional change to make it work.
Open the configuration dropdown in the toolbar and click *Edit Configuration*, then opening the *Use classpath of module* dropdown and select the one named **\[project name\].main**, that should be setup for both Minecraft Client and Minecraft Server.
8. In the end, you can test if you have set all things up successfully by running Minecraft Client Configuration. If all things go well, it will start a forge client and load your mod.
