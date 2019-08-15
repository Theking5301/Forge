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

## Custom Configurations
We will add this section in the future.

## Jenkins Integration
In recent time, Jenkins announced a brand-new plugin called [Blue Ocean](https://jenkins.io/projects/blueocean/) that aims to simplify the creation of pipeline and provide a clean and beautiful UI.
For open source project, you can take Blue Ocean as your first choice. 
However, on the other hand, Blue Ocean doesn't support closed source project (private repository), so you should use traditional way to create Jenkins project.

### Blue Ocean Setup
1. Open Blue Ocean and click the **New Pipeline** button at the top-right side.
2. Choose where you store your repository, we will take Github as the example.
3. If you have never used Blue Ocean below, it will ask you to create a personal access. Click the **create access token here** link.
If you have configured this before, just skip to step 6.
4. The link will take you to the personal access token settings page and checked all necessary permission, type the Note and then generate token.
5. After generating, you will see an access token and copy it back to the Blue Ocean input field and connect.
**Be caution that you can only see the access token ONCE.**
6. Choose the repository you want to integrate with Jenkins.
7. After the pipeline was created, it will clone repository from Github and start pipeline based on our predefined Jenkinsfile.
The pipeline result should be success. If something goes wrong, double check your setting. If you find this is one of our template's bug, it's no bother to create an issue [here](https://github.com/jenkins-example/Forge/issues/new) to let us fix the problem.
8. It seems that everything goes well in Jenkins, but we haven't finish our setup yet. 
Now, Jenkins can only check your repository when you actively start a new build, so we should setup webhooks to let Jenkins start build when a push was made or a pull request was opened.
9. Go to your github project's **Settings > Webhooks** page and click Add webhook button.
10. Type **http://\[your Jenkins hosting URL\]/github-webhook/** in the Payload URL field and select **Send me everything** radio below. Then click the Add webhook button below.
11. If all things go well, you will see a green check mark in front of your newly created webhook indicating your setting is working.
If it shows a warning mark, it might because your Jenkins server hasn't installed Github plugin yet. Please refer to your server administrator to solve the problem.
12. Ok, we have done our work. Try to commit some changes and enjoy the power of Jenkins' automatic integrations.

### Classic Jenkins Configurations
We will add this section in the future.
