# Guide To Set Up C/C++ Dev Environment

- [How To Read This Guide](#how-to-read-this-guide)
- [Windows](#windows)
	- [Using MinGW Installer](#using-mingw-installer)
	- [Using Chocolatey](#the-easier-way-via-chocolatey)
- [Linux](#linux)
- [MacOS](#macos)
  - [Why bother?](#why-bother)
  - [Getting GCC installed on MacOS](#getting-gcc-installed-on-macos)
  - [Issues with MacOS 13.0 Ventura and gcc-12](#unprecendeted-issue-with-macos-13ventura--gcc-12)
- [Compiling the code manually](#compiling-the-code-manually)
- [Setting up VS Code](#setting-up-vs-code)
	- [Installing](#installing)
	- [Compiling](#compiling)
	- [Running](#running)
	- [Code Runner](#code-runner)
		- [Windows](#windows-11)
		- [Linux and MacOS](#linux-and-macos)
- [Tips and Further Reading](#tips-and-further-reading)
	- [Code Runner](#code-runner)
	- [Do NOT guess how a piece of software might work](#do-not-guess-how-a-piece-of-software-might-work)
	- [Learn to search](#learn-to-search)
- [Authors](#authors)

### How To Read This Guide
This guide is meant for beginners as well as readers with basic knowledge. Most of the technical terms have been explained or have been linked to a webpage with more information.

If you still don't understand a term, just Google it :)

This guide explains how to install as well as use a C/C++ [compiler](https://en.wikipedia.org/wiki/Compiler) to run your code. The compiler used here is the [GCC](https://en.wikipedia.org/wiki/GNU_Compiler_Collection).

To write and edit code, any text editor such as Notepad can be used, although, a [code editor](https://en.wikipedia.org/wiki/Source-code_editor) is recommended because of syntax highlighting, code completion, and much more. Here, we will be setting up a popular cross-platform code editor - [Visual Studio Code](https://code.visualstudio.com/).

This guide has separate sections for different operating systems. Jump to the relevant section using the links below:
- [Windows](#windows)
- [MacOS](#macos)
- [Linux](#linux)

**NOTE**: You are supposed to enter and run a command in a _terminal_ whenever you are given one, in this blog.

A [Terminal](https://en.wikipedia.org/wiki/Terminal_emulator) generally refers to:
- [Command Prompt](https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/) on Windows.
	Windows also has [Powershell](https://en.wikipedia.org/wiki/PowerShell) and the new [Windows Terminal](https://en.wikipedia.org/wiki/Windows_Terminal) which combines all the different [shell environments](https://en.wikipedia.org/wiki/Shell_(computing)).
- Terminal on [MacOS](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac#:~:text=On%20your%20Mac%2C%20do%20one,%2C%20then%20double%2Dclick%20Terminal.) and [Linux](https://www.geeksforgeeks.org/how-to-open-terminal-in-linux/).

***

### Windows
Here, the native Windows version of [GCC](https://en.wikipedia.org/wiki/GNU_Compiler_Collection) - called [MinGW](https://en.wikipedia.org/wiki/MinGW) - will be installed.

There are quite a few methods to achieve this. We will be looking into two of them - one being the most widely popular; using the MinGW installer directly from its website - other being the simplest; using [Chocolatey package manager](https://chocolatey.org/).

Jump to the relevant method using the links below:
- [Using MinGW Installer](#using-mingw-installer)
- [Using Chocolatey](#the-easier-way-via-chocolatey)

#### Using MinGW installer

1. Download the installer file `mingw-get-setup.exe` from https://osdn.net/projects/mingw/releases/.

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199251856-1bd8f2ea-c745-4acc-987e-dc7114d13a95.png">

2. Run the `.exe` file. A window titled "MinGW Installation Manager" will open in a few minutes. In the **Basic Setup** tab, right-click the option named `mingw32-gcc-g++-bin` and click on `Mark for Install`.

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199252340-1395bea4-481b-4c62-b561-0b3cee96d18c.png">

3. Then on the top left corner click on `Installation > Apply Changes`. Continue through the rest of the installation process while keeping all settings as default. And then, you wait...

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199253213-bc0e83c9-135d-4878-a614-72b21f68eb04.png">

GCC is installed! Now we have to make it accessible by adding it to the [PATH](https://en.wikipedia.org/wiki/PATH_(variable)):

1. Go to `Windows Explorer > Right click on "This PC" > Properties > Advanced system settings > Environment Variables`.

	<img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/199253617-cad0a913-abb0-4aa9-820e-f733ee5e0d58.png">

2. At the bottom "**System Variables**" panel, look for a Variable named "**PATH**" and double-click on it.'
3. Click the “New” button to add a new path to Windows PATH.
4. Enter the Path of the folder to which you installed the GCC (by default, it's `C:\MinGW\bin`)

	<img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/199254777-a4f0d1b3-3de6-4b69-afd4-06e7fac1835d.png">

5. Press OK until you are out of the menus.

You should now have the GCC installed and ready to be used!
To verify, type `gcc --version` in [Command Prompt](https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/) and press enter; if you get an output stating its version, then it was successfully installed.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199273896-79ac8bef-0194-4721-a2ea-222a783708d1.png">


#### The easier way (via chocolatey)
Chocolatey is a package manager for windows that makes installing applications a lot easier and more automatable. As opposed to the long process we went through in the above way, via chocolatey the entire process of installing chocolatey can be reduced to just 3 commands - executed in an [Administrator Powershell](https://learn.microsoft.com/en-us/powershell/scripting/windows-powershell/starting-windows-powershell?view=powershell-7.2):

1. Install chocolatey with the instructions from their website: https://chocolatey.org/install
	- Run `Get-ExecutionPolicy` in an administrator PowerShell. If it returns **Restricted**, then run `Set-ExecutionPolicy AllSigned`.
	- Now run:
		```sh
		Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
		```
		and wait for the installation of chocolatey to be complete.

2. Close and reopen the admin PowerShell session.

3. Run `choco install mingw` and type `A` to confirm the installation.

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199414192-5f64e542-5925-4e39-b5e0-fba3b0b4cf0f.png">

	You should see this if it succeeds

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199414239-f1f93354-2f6f-491e-b17b-69b473664751.png">

4. Now run `gcc --version` to verify that it has been installed properly.

	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199273859-da553d60-59ae-49c6-9539-e9f305675c47.png">


***

### Linux
Most Linux [distributions](https://en.wikipedia.org/wiki/Linux_distribution) will have [GCC](https://en.wikipedia.org/wiki/GNU_Compiler_Collection) pre-installed. To check if it is installed:
```sh
gcc --version
```
If you get some output; NOT an error, then it is installed.

On [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu) and other Debian-based distributions:
Run the following commands in the [Terminal](https://itsfoss.com/open-terminal-ubuntu/):
```sh
sudo apt update
sudo apt install build-essential
```

> For other distributions just install the package `build-essential` from your package manager.

***

### MacOS

Though [GCC](https://gcc.gnu.org/) "_appears_" to be installed in MacOS by default but it's [clang](https://clang.llvm.org/) in disguise!

<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199031019-69c71f8d-80a0-4f8e-88bc-b37b17c1ed03.png">

#### Why bother?

For the audience one of the main drawbacks of using clang can be not able to use `<bits/stdc++. h>`, for your work.
To know about the differences in-depth - refer to:

- [From perspective of Apple; the developers of Clang](https://opensource.apple.com/source/clang/clang-23/clang/tools/clang/www/comparison.html#gcc)
- [From a neutral perspective](https://www.incredibuild.com/blog/gcc-vs-clang-battle-of-the-behemoths)

#### Getting GCC installed on MacOS

1. [Install homebrew](https://brew.sh/) - ignore if already present.
	- To check whether it is installed or not use the following command

		```sh
		command -v brew
		```

	- If the output is like the following then brew is installed!
		```sh
		~> command -v brew
		/opt/homebrew/bin/brew
		```

2. Installing [GCC](https://en.wikipedia.org/wiki/GNU_Compiler_Collection).

	```sh
	brew update
	brew upgrade
	brew install gcc
	```

	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/199038436-d28a2e50-bd44-47a8-ab85-f550355f2cf7.png">

	**Notice**: How the gcc is installed as `gcc-12` and `gcc` is still clang.

3. Now, you can either use `gcc-12` instead of `gcc`.
But if you want `gcc` to invoke the GNU version of gcc instead of clang then execute the following lines in your terminal. Since MacOS comes with
`zsh` by default we will be giving command for it only but if you have changed your shell then you must be equipped enough to do the following steps on that shell too - Right?

	```sh
	echo "alias gcc=/opt/homebrew/bin/gcc-12" >> ~/.zshrc
	```

	<img width="762" alt="image" src="https://user-images.githubusercontent.com/86282911/199040895-7540e4c5-3725-437d-a0e5-00bd7093ba87.png">

#### Unprecendeted issue with MacOS 13(Ventura) & gcc-12

<img width="1268" alt="image" src="https://user-images.githubusercontent.com/86282911/199091042-cd397043-5fa4-4745-8863-aa61fc1b107c.png">

If you are using MacOS Ventura and facing this issue - which means it's not fixed yet - no problem, then read the following issue/discussion to solve it!

- https://github.com/Homebrew/homebrew-core/issues/113968

**Yes. You are going to read all of that, try to understand; try to fix. Repeat until you succeed!**
You have to start self-learning sometime later, so why not start now?

***

### Compiling the code manually

Follow these steps to compile your `.c` file manually.

1. Create a file with the name `first_c_program.c` with the following content in it and then save it.
	```c
	#include <stdio.h>

	int main(){
		printf("Hello World!");

		return 0;
	}
	```

	> ⚠️  Make sure you don't have spaces in your filename!

2. Compile the program and execute it. You can replace `executable.exe` with `anything.anything`.

	<img width="533" alt="image" src="https://user-images.githubusercontent.com/86282911/199065183-33f31329-cb4d-48d9-9639-b9d65a1d7df7.png">

	For Windows users, the command to run will be the following, the above works for Linux & MacOS only.

	```sh
	.\filename.exe
	```

***

### Setting Up VS Code
[Visual Studio Code](https://code.visualstudio.com/) is a free and open-source code editor that is customizable through [extensions](https://marketplace.visualstudio.com/VSCode). The [C/C++ extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) can be used for compiling and running C/C++ code along with many more features.

#### Installing
1. Open VS Code
2. Open the extensions panel using the button on the left or by pressing `Ctrl+Shift+X`.
3. Search and install the C/C++ extension.

	<img width="400" alt="image" src="https://user-images.githubusercontent.com/86282911/199403927-ff784c57-ccd4-4cd2-a07b-5e043f28c876.png">

Once the extension is installed, creating or opening any `.c` or `.cpp` file will have syntax highlighting, code completion, and other features.

<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/199404180-38e125a6-139a-42c8-bde2-b367d889440c.png">

#### Compiling
To compile the code, open a file and run `Terminal > Build Task` from the main menu or press `Ctrl + Shift + B`.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199404707-95b1ad79-b55c-474f-b68c-4e782513a675.png">

**On Windows**: From the dropdown, select `C/C++: g++.exe build active file`(for C++ files) or `C/C++: gcc.exe build active file`(for C files).

**On Linux and MacOS**: From the dropdown, select `C/C++: g++ build active file`(for C++ files) or `C/C++: gcc build active file`(for C files).

<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199405213-fba62742-82c2-4e00-9fe9-cc6de50c755e.png">

#### Running
Once the code has been compiled, an [executable](https://en.wikipedia.org/wiki/Executable) file will be created (with the same name as the code file). On Windows, this file will have a `.exe` extension on Windows and no extension on macOS and Linux.

To run the file:
1. Open the VS Code [integrated terminal](https://code.visualstudio.com/docs/terminal/basics) by pressing **Ctrl + \`** .
2. Type:
	- **On Windows**: `.\` followed by the name of the executable file.
	- **On Linux and macOS**: `./` followed by the name of the executable file.

	and press enter.
	
	<img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/199405926-82af17c6-3cea-45d0-a4ef-d0f4329353de.png">

3. The output of the code will be visible in the terminal!

### Code Runner

Depending on your OS, we suggest different code runners. Hop into the section of your interest:

- [Windows](#windows-11)
- [Linux and Macos](#linux-and-macos)

#### Windows 11

> You are suggested to use [code-runner](#linux-and-macos) using [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) instead of using this buggy `.run` extension which will be installed in this section ahead - which is shared just as an alternative which is relatively easy to setup.

1. Click on the extensions icon (<img width="20" alt="image" src="https://user-images.githubusercontent.com/86282911/201152366-5c50d509-8058-4e14-ac59-75697f2bcb30.png">).
2. Search for `code runner`.
3. Install the extension shown in the screenshot below.

<img width="1283" alt="image" src="https://user-images.githubusercontent.com/86282911/201151700-83ac022a-0b7e-411a-9337-a8cf50f1f333.png">

#### Linux and MacOS

For simplicity and to automate a few steps for a list of languages you can try [code-runner](https://github.com/proffapt/code-runner).
<img width="603" alt="image" src="https://user-images.githubusercontent.com/86282911/199088479-26cce835-c9bc-414d-9bc4-5de188145c92.png">

##### Installation

Copy and paste the following command in your terminal and wait for the final message - you are done!
```sh
curl https://raw.githubusercontent.com/proffapt/code-runner/main/setup.sh | /bin/bash
```

Can help in the following ways:
- Just one command to compile and execute the compiled file: `run filename.extension`.
- Cleans compiled binary by default. So, that you don't submit binary instead of a `.c` file in your assignments.
- Detects the version of python to be used ( accuracy of 95% ).
- Can be used to create a file with _spaces_ in its name ( vs-code runner extension lacks this )
- Can be used to execute a file in a different directory ( vs-code runner extension lacks this; and limits some functionalities )
- Inbuilt debugger support.
- Integrates with [NeoVIM](https://neovim.io/) and [VS-CODE](https://code.visualstudio.com/) - steps in the documentation of the tool.

> And many more, read the documentation and code for a thorough understanding at https://github.com/proffapt/code-runner.

***

### Tips and Further Reading

#### **DO NOT GUESS** how a piece of software might work.

When using a tool for the first time, you **CAN'T** and **MUSTN'T** guess how it works! Beginners often make this mistake and waste a lot of their time and of others too; without even searching or reading the docs!<br>
Rather read the documentation/help for that program or just simply search for whatever you wanna achieve with that tool.

> [Read The Fucking Manual - RTFM](https://en.wikipedia.org/wiki/RTFM#:~:text=RTFM%20is%20an%20initialism%20and,forum%2C%20software%20documentation%20or%20FAQ.)

#### Learn to search!

This is a starting guide, so it was a bit explanatory. What we promote is **self-learning**.
The basic idea behind it is very simple:
<img width="150" alt="image" align="right" src="https://user-images.githubusercontent.com/86282911/199060464-2dde3274-68dc-42e8-bc3d-e0e561d6e04b.png">

1. Read the error carefully and try to understand it.
2. Phrase your problem/goal.
3. Search it on your favorite search engine **before asking in groups**.
4. Either you will get the solution, if not then ask in groups/forums.

***

### Authors

- Arpit Bhardwaj ([@proffapt](https://github.com/proffapt))
- Harsh Khandeparkar ([@harshkhandeparkar](https://github.com/harshkhandeparkar))
- Jeffrey Samuel ([@signor-koala](https://github.com/Signor-Koala))

<p align="center"> Created with lots of <b>&lt;/&gt;</b> and ♥ </p>
