---
description: Interact with your scripts using WayScript's command line interface
---

# CLI Tool \(alpha release\)

The CLI tool can be used to sync files between your WayScript file system and your local machine and run your scripts from the command line. 

{% hint style="danger" %}
Please note that the WayScript CLI tool is in alpha development stage. Please reach out to us at nihar@wayscript.com or on Discord if you experience any unintended behavior.  
{% endhint %}

## Installation

```bash
$ pip install wayscript-cli
```

#### System requirements:

* Latest Python distribution \(version 3.6 or higher\)
* Latest version of pip package manager \(version 20.0 or higher\)

## Initial Setup

### Step 1: Enter your WayScript credentials

```
$ wayscript configure
```

#### **The tool will prompt you to enter the following required fields for authentication:** 

* WayScript username or team name
* WayScript API key \(from your account or team settings\)

{% hint style="info" %}
You have one WayScript account or team configured at a time, but you can use the `wayscript configure` command at any time to switch the tool to use a different account or team's credentials. 
{% endhint %}

### Step 2: Choose a local directory for your WayScript files

* Navigate your local machine's current directory to where you would like to store your WayScript files
* The CLI tool will create a directory within the current directory with the same name as your account or team name, so please ensure there will be no files or folders with conflicts

### Step 3: Pull your WayScript file system

```text
$ wayscript pull
```

The CLI tool will initialize the WayScript directory and then fetch your entire WayScript [file system](../getting_started/file-system.md) into the current directory on your local machine. 

## On-going Usage

```text
$ wayscript pull
```

#### This command executes the following actions:

* Fetches your WayScript file system \(stored on WayScript's remote servers\) for your configured account or team
* Compares the WayScript file system against the files in your local machine 
* For any files in your local machine's current directory and any nested directories:
  * If the file has been modified or created in your WayScript file system, the tool will replace your local file with this version or add this file in the correct directory
  * If the file has been modified on your local machine, the tool will ask if you would like to overwrite this file on your local machine with the version in your WayScript file system

```text
$ wayscript push [file path]
```

**This command uploads your current directory on your local machine with the WayScript file system.**

**Optional arguments:**

* `file path` to file or folder within you wish to push \(instead of entire current directory\)

**Key considerations:**

* If any files fail to upload, they will be indicated in the output. Here are few common instances where your file may fail to upload:
  * `<script name>.ws` file is not properly formatted
    * This can occur if you make a breaking change to the `.ws` file
    * To avoid this issue, please do not attempt to create a new module or modify the special characters that signify an existing module within the `.ws` file
  * Moving or renaming protected files
    * Moving a `.ws` file outside its initial script directory or renaming the file
    * Moving the account or team directory or script directory outside the folder initialized as the WayScript directory or renaming the directory
* The `push` command cannot rename or delete any files that were modified on your local machine
  * Any files that are renamed will generate a new file in the WayScript file system
  * Any files that are deleted will be retained in the WayScript file system

```text
$ wayscript run [script name] [--function 0] [--trigger 0] [--args '["hello", "world"]']
```

**This command runs your script from the WayScript file system.** Please not the CLI tool will not execute files on your local machine that have not been pushed to the WayScript file system.

**Optional arguments:**

* `script name` - script name must be specified if your current directory is not inside the script folder
* `--function <integer>` - run only a specified function within your script using the function index \(with the left most function in your script tree having an index of 0\)
* `--trigger <integer>` - run only a specified trigger within your script using the trigger index \(with the top most trigger in a function having an index of 0\)
* `--args <array of values>` - pass values into a function's input variables

## Editing the \`.ws\` file

### Example file

```text
󰀇 m.0 - py
# connect a variable above and read its value from the variables dictionary:
print( 'variable values:', variables )

variables[ 'First_Output' ] = 'Test'
󰀇 m.3 - js
// connect a variable above and read its value from the variables dictionary:
console.log( 'variable values:', variables );

variables[ 'First_Output' ] = 'Testing';
```

{% hint style="warning" %}
Each code module is identified by a line with metadata in the format:  `󰀇 m.0 - py` . Editing the line with this identifier will cause unintended behavior when using the CLI tool. 
{% endhint %}

{% hint style="success" %}
For those that develop within Visual Studio Code, our team has developed an extension to reintroduce code language syntax highlighting so you can easily write code within your script's `.ws` file. You can download it here: [https://github.com/wayscript/ws-syntax-extension](https://github.com/wayscript/ws-syntax-extension). 
{% endhint %}

