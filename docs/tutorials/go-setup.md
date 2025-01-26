# Setting up a dev container for Go

* Primary author: [Shriyans Sapkal](https://github.com/shrithebee1)
* Reviewer: [Nick Kaplan](https://github.com/NickKaplan64)

## Prerequisites
Before starting this tutorial make sure you have the following:

1. A Github Account: Create one for free [here](https://github.com/).
2. Git Installed: You can install it [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
3. Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
4. Docker Installed: Install Docker from [here](https://www.docker.com/products/docker-desktop).

## Part 1: Setting Up Project Repository
### Create a Local Directory and Initialize Git

1) Open terminal or command prompt

2) Navigate to a folder you would like your project to be held in and create your directory:

```sh
mkdir HelloWorldGo
```

3) Enter the folder:

```sh
cd HelloWorldGo
```

4) Initialize a new git repository:

```sh
git init
```

5) Create a README file:

```sh
echo "# My new Go Project" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Create a Remote Repository on GitHub

1) Login to your GitHub account and navigate to the [Create a repository page](https://github.com/new)

2) Fill in any following details:

- **Repository name:** HelloWorldGo

- **Description:** "Starting a Go Project to print 'Hello World' out"

- **Visibility:** Public

3) Do not initialize the repository with a README, .gitignore, or license

4) Click **Create Repository**

### Link your Local Repository to GitHub

1) Add GitHub repository as a remote:

```sh
git remote add origin https://github.com/<your-username>/HelloWorldGo.git
```

Replace ```<your-username>``` with your GitHub username.

2) Ensure your branch's name is main and push to the remote repository

```sh
git branch -M main
git push --set-upstream origin main
```