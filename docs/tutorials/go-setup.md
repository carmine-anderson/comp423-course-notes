# Setting up a dev container for Go

* Primary author: [Carmine Anderson - Falconi](https://github.com/carmine-anderson)
* Reviewer: [Elijah Wood](https://github.com/ElijahWood2003)

#
# **Welcome**!!!
Welcome to my tutorial on creating a "Hello World!" program using Go. Go is a programming language that is an open source project, allowing programmers to be more productive. As an expressive, concise, clean, and efficient language, Go allows you to utilize it's concurrent mechanisms to write programs that get the most out of multicore and networked machines. 
#
???+ warning "Warning"
    You've got this, lock in, we're loaded baby.

<!-- ## What will you learn:
* How to create and enstablish a new Dev Container to build the program in
* How to initialize a new repository -->

## Prerequisites
Before we can begin to create a dev container for Go, we must make sure that we have already taken some preliminary steps that must be done before creating the container and producing our program.

* Create a [Github](https://github.com/carmine-anderson) Account / make sure [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) is installed.
* Download [Visual Studio Code](https://code.visualstudio.com/) / Required extensions
* Download [Docker](https://www.docker.com/products/docker-desktop/)

# Part 1: Project Setup: Creating the initial Repository
## Step 1: Using git to create a local directory
1. Open the terminal or command prompt (cmd.exe)
2. Create a new local directory for your project using the following command. (Create this directory anywhere that you would like, default location is fine.):
```
mkdir go-setup-proj
cd go-setup-proj
```
3. Now we initialize a new git repository by running:
```
git init
```
4. Create a README.md file:
```
echo "# Go Program" > README.md
git add README.md
git commit -m "Initial commit with README"
```

## Step 2: Create a remote repository on Github
1. Login to your Github and go to the [new repository page](https://github.com/new).
2. Fill in the following details:
    * Repository Name: ``` go-program```
    * Description: ``` A new and simple go program.```
    * Visibility: ```public```
3. Make sure that you have unchecked the initialization with a README, .gitignore, and lisence. 
4. Create the repository and clone it to your machine via:
```
git remote add origin https://github.com/<your-username>/go-program.git
```
5. Your default branch should be named "main", if it is not, you can change it by running:
```
git branch -M main
```
6. Now you can push to your remote repository by running:
```
git push --set-upstream origin main
```


# Part 2: Setting up the actual Development Container/Environment
## Step 1: Setting up Configuration for the Go Dev Container.
1. Open the ```go-program``` directory in VS code and make sure you have the Dev Containers extension on VS code as well.
2. Create a ```.devcontainer ``` directory (folder) in the root of your project folder.
3. Create a ``` devcontainer.json``` file inside the ```.devcontainer``` directory. This file actually holds the configuration for the dev container.
4. Copy the config file data below and put into your ```devcontainer.json``` file.
5. Now that you are ready to open the project, we can now do this in a container. To do this, hold down ```command(or control on mac) + shift + p```, type ```reopen in container``` in the search bar and click on the first one that pops up. (This process could potentially take a while)
```
# Config File Data for step 4 (Copy starting from the first { )

{
  "name": "Go Program",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
  "features": {
    "ghcr.io/devcontainers/features/go:1": {
      "version": "latest"
    }
  },
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": [
        "golang.go"
        ]
    }
  }
}
```
???  "STEP 5: Important information about the configurations file!"
    ??? "name"
        ```name```: A descriptive name for the dev container
    ??? "image"
        ```image```: This is what docker uses in the container to use the language, in this case, it's for go.
    ??? "customizations"
        ```customizations```: This housed important configurations to VS code that you find and use. For this project, we will find VS code extensions that we will need for this project. 

# Part 3: Making your first Go project
## Step 1: Lets Get Go(ing)!
??? abstract "The Go Language (Golang)"
    Go, also commonly referred to as "Golang", is an open-source programming language designed by Google. It also has alot of practical and useful mechanisms:
    ???+ "Performance:"
        Go is a compiled language, meaning that it is fast like C or C++.
    ???+ "Simplicity:"
        With clean syntax, which is also straightfoward, allows for ease of learning.
    ???+ "Concurrency:"
        Go has built-in support for concurrent programming using Goroutines and Channels
        ??? "What are Goroutines?"
            A lightweight thread of execution that is managed by the Go runtime.
        ??? "What are Channels?"
            Channels are a built-in data structure that allow Goroutines to communicate and synchronize with each other. 

In order to create a go program, you must in fact have the language ```Go```. This should have been done through the Dev Container (devcontainer.json) file that we created.

To ensure that you have ```Go```, you can run the following command in your terminal/bash
``` 
go version
```

## Step 2: Beginning your Go project
Once ensuring that you have go, you can follow the next steps:

- Initialize a Go module: 
```
go mod init hello-comp423
```
- Create a new file named ```main.go``` with the following added into the file:
```
package main

import "fmt"

func main() {
    fmt.Println("Hello, COMP423!")
}
```
- You should then run the program directly through bash using the following command:
```
go run main.go
```
- Output:
```
Hello, COMP423!
```
???+ warning "Warning"
    If your output is incorrect, check spelling errors, importing (package) errors, or indentions.

## Step 3: How to 'Build' the program.

???+ "What are we building?"
    To build a program means to compile it's 'source' code into 'executable' binary. The go compiler takes in your ```.go``` files and produces its own file, that can run directly without needing any more runtime, or a seperate interpreter.

    ??? "More simplified"
        You write code in .go files.

        Run ```go build```, and it generates an executable.

        You can then run the executable on its own.

- Build the binary: (this will establish and create the executable file named hey)
```
go build -o hey main.go
``` 
- Run the built binary directly
```
./hey
```
- Output:
```
Hello COMP423!
```
## Extras
There are two different types of "build-type" processes, one is ```run``` and the other is ```build```.

- ```go run``` Compiles and runs code at once, without the creation of a standalone executable file. While ```go build``` compiles and generates a standalone executable file, allowing you to run the code without the go language installed. 

# **Let's GOOOOOOO, Success!!**
???+ Success "You've officially created your first program using the language Go."
    Good Job!!! 
    
    :)

Lets push your changes to your github repo.

- Lets add the changes to the staging area:
```
git add .
```
- Next, lets commit the changes:
```
git commit -m "First offical Go"
```
- Push it...
```
git push origin
```

## Sources
- [SquidFunk Extensions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#inline-blocks-inline-end)
- [Starting a Static Website - Kris Jordan - RD06](https://comp423-25s.github.io/resources/MkDocs/tutorial/#step-2-configure-your-site)
- [Go Documentation](https://go.dev/doc/)