---
order: 2
icon: git-pull-request
---
# Contributing
!!!warning
This page is a stub. Feel free to help contribute by creating a [pull request](https://github.com/lunauii/bcit-resources/pulls)!

Reason: **currently missing Editing Guidelines section**<br>
Latest Update: **09 January 2025**
!!!
## Basics
### Pre-requisites :icon-question:
Ensure that before contributing, you have basic knowledge of the `git` CLI tool as well as are semi-familiar `GitHub`.

An IDE or text editor is not needed due to the wiki being editable in the development build, but can be used if you want a wide overview of the code or just
prefer coding in one in general.

!!!Popular IDEs/text editors for web development include:
- Visual Studio Code (https://code.visualstudio.com/)
- Brackets (https://brackets.io/)
- JetBrains WebStorm (https://www.jetbrains.com/webstorm/)
!!!

You must also have the `retypeapp` package installed. Instructions are provided on Retype's [Quick Start guide](https://retype.com/guides/getting-started/).

!!!warning
You *can* contribute to the source code without `retypeapp`. However, you will not be able to see a live preview of your code on a page.
!!!
### Forking :icon-repo-forked:
To begin helping out, you must first **fork** `lunaui/bcit-resources` on GitHub and create a remote instance of it on your machine. Leave the repository name the same as-is, unless you want to fork it for other purposes.

!!!
To fork this project, go to the repository [on GitHub](https://github.com/lunauii/bcit-resources) and press the [!badge variant="info" text="Fork :icon-repo-forked:"] button near the top-right of the page.
!!!

Navigate to that repository and take note of the URL, you will need it for the next section.

### Cloning :icon-repo-clone:
Clone the repository into a location of your choosing and then change directories to it. For demonstration purposes, I am going to be cloning the bcit-resources folder into the user's Documents folder.

Replace `lunaui` with your Github username, and `usr` with your machine's user's name.
+++ Windows
```bash
cd C:\Users\usr\Documents
git clone https://github.com/lunaui/bcit-resources.git
cd bcit-resources
```
+++Linux
```bash
cd /home/usr/Documents
git clone https://github.com/lunaui/bcit-resources.git
cd bcit-resources
```
+++MacOS
```bash
cd /Users/usr/Documents
git clone https://github.com/lunaui/bcit-resources.git
cd bcit-resources
```
+++

### Testing and Editing :icon-beaker:
To see a live preview of the page while the code is being edited, run the following command while still in the git directory:
```bash
retype start
```
A localhost server of the development build will be opened, allowing you to see changes in real time.

While serving the page this way, you can either directly edit the files with the [!badge text="edit"] button on the top right of any given article while in the development build, or you can edit the files with an IDE or text editor. 

Both solutions are, at baseline, functionally identical.

### Pull Requests :icon-git-pull-request:
In order to save the changes to *this* website and not just the copy you have on your machine, you will have to create and send a **pull request**.

To do this, first ensure all your changes have been pushed already.
```bash
git add .
git commit -m "{insert meaningful commit message}"
git push
```
!!!
It is recommended to commit your changes frequently and often before pushing instead of dumping your push into one massive commit.
!!!

Go to your repository on github. You should see a button above the file list called [!badge variant="info" text=":icon-git-pull-request: Contribute"].

Create a pull request with a meaningful title and description describing what you have changed with your commits. After that, create the pull request with the corresponding button.

If your changes get approved (it probably will), you will see your changes on the website take effect!

!!!info Regular Contributors
If you are a regular contributor or have made guides in the past for CST, ask me on Discord (`lunaui`) for **Collaborator** access to the repository so that you can bypass me needing to approve your pull requests or even approve other's pull requests yourself!
!!!

## Editing guidelines
*TODO: cover discrepancies between BBY and DTC*