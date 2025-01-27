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

## Part 2: Setting Up Dev Container

1) In VS Code open your HelloWorldGo folder

2) Install the **Dev Containers** extension for VS Code

3) Create a ```.devcontainer``` directory in the root of your project and add a file into the folder called ```devcontainer.json```

4) Inside the ```devcontainer.json``` file add the follwing code to setup our environment:


  * **name**: This specifies a clear, descriptive label for your development container.
  * **image**: Defines the Docker image used to create the container. For this setup, we'll use the latest Rust environment image provided by Microsoft.
  * **customizations**: Allows you to configure additional features in VS Code, such as pre-installing useful extensions. Adding extensions here ensures other developers on your project have them installed in their dev containers automatically.

```json
{
  "name": "Hello World Go",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.Go"]
    }
  }
}
```

???+ info "Extension"
    The ```golang.Go``` extension was developed by Google engineers and provides extensive language support for the Go language in Visual Studio Code. It was released in 2015.

5) Reopen the project in a container by pressing ++ctrl+shift+p++ or ++cmd+shift+p++ and then selecting **Dev Containers: Reopen in Container**

## Part 3: Creating the Go Project

1) In the terminal, confirm Go is installed using ```go version```

2) To create a Go Module use the command:

```sh
go mod init HelloWorld
```

???+ note "Purpose of ```go mod```"
    This command manages modules in Go projects which allows for the management of dependencies in Go projects. It also tracks version of dependencies used and ensures a consistent development environment. It is similar to a ```requirements.txt``` in Python.


3) Create a file ```hello.go``` and paste the following code

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")
}
```

???+ note "```main``` package and import statement"
    The ```main``` package indicates that this file is the main file. It will be run by default when ```go run . ``` is run.
    The ```"fmt"``` package provides functions for formatted input and output operations. It serves the same purpose as ```<stdio.h>``` in C.


4) In the terminal you can then run your code using:

```sh
go run .
```

You should see ``Hello COMP423!`` output to your console 

5) Optionally you can first build an executable file using:

```sh
go build hello.go
```

6) Then you can run the executable in terminal using: ```./hello```

???+ warning
    If you wish to preserve the binary of the built program, **do not** use ```go run .```, instead use the above two step process.




<br>
<br>

[^]:
  Steps regarding git and dev container initialization were taken from the [COMP 423](https://comp423-25s.github.io/resources/MkDocs/tutorial/#step-1-create-a-local-directory-and-initialize-git) site.