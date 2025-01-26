# **Tutorial : Setting up a Dev Container for Go**

* Primary author: [Benjamin Corter](https://github.com/bjcorter)
* Reviewer: [Reece Corter](https://github.com/reece333)

### **Prerequisites**

First off, ensure you have the following installed on your machine:

* Docker
* VS Code
* Dev Containers extension for VS Code
* Git

## **Step-by-step Instructions**

1. Create a Blank Directory and Initialize Git
    * Open your terminal and go to the location you want your project to be
    * Create a new directory for the project
    ```
    mkdir go-devcontainer
    cd go-devcontainer
    ```
    * Initialize a new Git Repository
    ```
    git init
    ```
1. Set up the Dev Container
    * Create a ".devcontainer" directory in your project directory
    ```
    mkdir .devcontainer
    cd .devcontainer
    ```
    * Create a "devcontainer.json" file in your ".devcontainer" directory and add the following to it: 
    ```
    {
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:1.20",
    "customizations":  {
        "vscode": {
            "extensions": [
                "golang.go"
            ]
        }
    },
    "postCreateCommand": "go mod init example.com/go-devcontainer"
    }
    ```
    !!! info
        * "name" is the name of the container
        * "image" is the base container image for developement in Go
        * "customizations"-"vscode"-"extensions" installs the Go extension for VS Code in you container
        * "postCreateCommand" initializes a Go module as soon as the container is made, and this module is how all of the dependencies are managed
    * Return to the root of your project
    ```
    cd ..
    ```
1. Open the project in your new Dev Container
    * In the terminal, run:
    ```
    code .
    ```
    * VS Code will then prompt you to reopen the project in the Dev Container
        * Select "Reopen in Container"
    * After Opening the Container, verify the Go version you are using
    ```
    go version
    ```
1. Write the "Hello Comp423" Program
    * In the Dev Container, create a new file named "main.go"
    ```
    touch main.go
    ```
    * Open "main.go" and implement the following program:
    ```
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello Comp423")
    }
    ```
1. Compile the Program
    ```
    go build -o hello-comp423 -buildvcs=false
    ```

    !!! note
        When working through this tutorial to ensure its effectiveness, I initially did not have the "-buildvcs=false" and an error was thrown, and the terminal told me to add this, and it worked. I'm not entirely sure as to why, but I believe it has something to do with the Version Control System.
    
1. Run the Program
    ```
    ./hello-comp423
    ```

    !!! tip
        You could also use the command:
        ```
        run main.go
        ```
        The key difference here is that the "build" command outputs an executable file with the name after the -o flag, while the "run" command simply compiles and runs the program all together

**You have now successfully created a dev container and made a simple project in the Go programming language!**
