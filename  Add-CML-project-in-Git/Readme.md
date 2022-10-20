# Simple approach to set up a CML project on Github as a part of CML or CDE SPARK Development

## Context: 
If you have started using Cloudera machine learning and are setting up your ML Project, and are at a point where you want to set up a git repo to collaborate and distribute your work, then this tutorial provides you an easy set of steps to do so, by working directly working in theCML platform without switching out of the platform IDE.

**IMPORTANT WARNING / DISCLAIMER** - These steps will put your code into an external repository, please make sure you understand that you are now publishing your code externally and be cognizant of copyright and properitory implications that brings when you initiate this. 

## Pre-requisites: 
- This tutorial outlines the process of using a public git repository on github. A subsequent
guide will be published on how to follow this process for a private git repo for an organization. 
- You already have an account in Github. If you do not go to github.com and follow the steps to create a new github account
- You have access to a Cloudera Machine Learning platform and are able to access a workspace and create new projects. 



## Additional Git References

- [Adding locally hosted code to github](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github)
- [Creating a Personal Acccess Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

## Description 
Git has been one of the go-to choices for developers for versioning, collaboration, code commit and restore and CI-CD. If you have been using cloudera machine learning for development, this guide provides you an easy way to use your CML workbench to setup a remote Github repo. In this guide we will do the following
- **Create a remote github repository**
- **Create a sample cml project**
- **Use simple Github CLI commands to connect to the remote repository in step 1 to push your cml project to the remote repoository**

### Step 1 : Create a default CML Project  : 
- Launch CML from CDP Control pane and select the workspace where would like to set up this demo project for version control 
<br>
<br>
![alt text](./Images/launch-project.jpg)
- After clicking  on the new project enter the details for a sample project <br> <br>
![alt text](./Images/NewProject.png) <br>
- This creates a new project with a set of default folders. Check that your folder structure looks like below  <br> <br>
![alt text](./Images/Default-project.png)
- Next launch a default session with Workbench and basic configurations <br> 

### Step2 : Setting up the Github repo on Github server
- Got to www.github.com , sign in with your user id
- On the top right corner click on "+" sign and add Repository
![alt text](./Images/Create-new-repository.jpg)
- Add the repository details as below
![alt text](./Images/Create-Repo.jpg)
- After saving the repository, check that you can see the repostory listed in the repo home. Open this repo and copy the path of the repository. Your repoistory should have the format https://github.com/<your-user-name>/git-version-demo 
![alt text](./Images/Repo-home.jpg)
- Next click on your Github profile icon on the top right to go to Git hub settings<br>
![](./Images/Profile-Menu.jpg)
- Click on menu option and developer settings option <br>
![](./Images/developer-settings.jpg)
- Click a new personal access token that you can use to connect to public git from CLI.<br>
![](./Images/Personal-access-token.jpg)
- After you complete the previous step, ake sure you have copied the generated token somewhere.<br
![](.//Images/GeneratedToken.jpg)

This completes all the steps on the public Github that you needed to do to set up a remote repository. In the next step we will learn how to connect to this repository from Cloudera Machine Learning service. 

### Step 3 
- Come back to your project in Cloudera Machine Learning workspace that you had created earlier and start a new session with default settings ( you can use any editor , since we will not be working with the editor , it really does not matter which one you choose)
![alt text](./Images/New-session.png) <br><br>
- Once your session is spun off, click on Terminal access from the top menu to launch a new terminal for your session. <br> <br>
-![alt text](./Images/terminal-access.jpg) 
- Now we will add the current project files shown in the terminal to our remote repository
-![alt text](./Images/terminal-details.jpg)<br> <br>
<br>
- Next we will use some commands to push the contents of our local project to the remote repository

1. Initialize the local repository <br> 
    `git init `
    
2. Use the path to the remote Github repo you copied earlier to set up a remote name for the repo in CML or change the your-github-user-name to your github id you used earlier to create the repo <br>
    `git remote add origin https://github.com/your-github-user-name/git-version-demo`

3. Let us list the remote repos now <br>
`git remote -v`

4. Finally get the status of the repo. This gives us the list of files in the project that we would now like to add to our remote repository. Git commands can be used to ignore certain files as well, but for now well add all these files.<br>
`git status` <br> <br>
Below is the output you should see after running these commands on terminal at the end of step 4 <br><br>
![alt text](./Images/cml-terminal.jpg)

5. Next let us add all these files for version tracking and make our first commit <br>
`git add .` <br>
`git commit -a -m "first git commit"` <br>
Below is the output after running these commands that you can refer to.
![alt text](./Images/git-initial-commit.jpg)
6. Finally you need to create a branch called main and  push these commited files to the main branch <br>
`git branch -m Main`<br>
`git push origin main`<br>
you will be asked to login to your Gitaccount. Use your userid and the personalized access token that you copied to enter here. The output looks like this.
![alt text](./Images/cml-terminal-2.jpg) <br><br>
7. Finally, as a last step we will go back to the github public repo to check if our changes are indeed pushed to the repo. here is the output of the earlier empty repository , which now contains my CML project. 
![alt text](./Images/Validate-in-githu.jpg)

## Summary
in this guide,  we learnt how to add an existing code artefcts in Cloudera Machine Learning Platform that you would create as a part of your Machine learning workflow or for Spark jobs on CDE to a repository on a public github. Github provides a large set of commands that can be used on CML Command line terminal for working with your remote repository. For more information check out additional documentation on github.com




 




