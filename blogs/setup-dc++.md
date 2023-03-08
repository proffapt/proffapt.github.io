[^1]: [Which campus has highest total share and users on DC++ in India?](https://www.quora.com/Which-campus-has-highest-total-share-and-users-on-DC++-in-India). Quora. Retrieved May 1, 2015.

# DC++

IIT Kharagpur __once had__ one of the largest DC ([Direct Connect](https://en.wikipedia.org/wiki/Advanced_Direct_Connect)) networks in India[^1]. It lost its glory when the pendamic hit and everything went online. This is an effort to restore that glory back, by educating students about "_How can one connect to the DC Hub properly_". Following is the structure of this documentation for a quick overview and easy navigation.

- [Installing the client](#installing-the-client)
- [Configuring the client](#configuring-the-client)
- [How to share content](#how-to-share-content)
- [Some common issues](#some-common-issues)
- [Installing mono fonts](#installing-mono-fonts)

## Installing the client

Users connect to hubs using DC clients, and are able to share files with each other at high speeds. The most popular hub is [HiT Hi FiT Hai](https://wiki.metakgp.org/w/HiT_Hi_FiT_Hai).<br>
There are various DC clients available for differenct platforms. To name a few, we have<br>
|Platforns|Client(s)|
|---------|---------|
|Windows|EiskaltDC++, DC++|
|Linux|EiskaltDC++, LinuxDC++, ncdc|
|MacOS|EiskaltDC++, Shakespeer, ncdc, Mac DC++|
   
However, it is recommend to use [Eiskalt DC++](https://sourceforge.net/projects/eiskaltdcpp/files) for uniformity across different platforms.<br>
To install EiskaltDC++ on your platform of interest refer the following links:
- [Windows](#windows)
- [Linux](#linux)
- [MacOS](#macos)

#### Windows
   
[Download Eiskalt DC++](https://sourceforge.net/projects/eiskaltdcpp/files/Windows/).<br>
Go through the basic installation setup and install it.

#### Linux

Install Eiskalt DC++ on __debian based distros__ like - _ubuntu, linux mint etc_ using the following command
```sh
sudo apt install eiskaltdcpp
```
> **Note** If you are not on debian based distro, search for the package name using the package manager your distro uses and install it.

#### MacOS
	
- [Install Homebrew](https://brew.sh/) - _skip this step if already present_.
  - To check whether it is installed or not, use the following command
    ```sh
    command -v brew
    ```

  - If the output is like follwoing, then brew is installed!
    ```sh
    ~> command -v brew
    /opt/homebrew/bin/brew
    ```
 
- Install Eiskalt DC++ using the following command
  ```sh
  brew install eiskaltdcpp
  ```

## Configuring the client

1. Open Eiskalt DC++ & press the following keyboard shortcut to open its __preferences__ window according to your platform
   |Platform|Shortcut|
   |--------|---------|
   |Windows|`ctrl + o`|
   |Linux|`ctrl + o`|
   |MacOS|`cmd + ,`|

3. Set a `Nick` aka _username_ for your current instance.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223125464-437cbbc0-4e88-46ab-aa5c-a72adf9ba3a8.png">
	
	> **Note** The __Nick__ must be unique.

4. Now Goto: `Connection` > `Advanced` > `TLS settings` and choose `Allow TLS`.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223126546-7bbd64fd-e098-4427-91f0-0eaaf80c1ef1.png">

5. In order to render the _welcome message_ aka `Message of The Day` properly you need to set a mono font for the client GUI.<br>
	To do so Goto: `GUI` > `Fonts`, then select any __mono__ font available on your system.<br>
	You will need to double click on the fonts to change them.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223131317-2b5329b3-abda-48d3-b1bd-b0f531c4b841.png">
	
	> **Note** If you don't have any `mono` font installed on your system then refer to the section [Installing mono fonts](#installing-mono-fonts) for installing one based on your platform

6. Now press `Ok`. 

7. Press the following key combination for quick connect dialogue, according to your platform.<br>
   |Platform|Shortcut|
   |--------|---------|
   |Windows|`ctrl+n`|
   |Linux|`ctrl+n`|
   |MacOS|`cmd+n`|

   Enter the current IP for DC++. At the time of writing this blog it is `10.105.12.22`. Press `Ok`.<br>
	<img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/223131882-7e86be2e-d96e-44e3-ad4b-bca4be98b621.png">

8. You should now be connected to the hub and if the fonts are set properly you should see something like this. <br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223134018-c1f1c1f2-4272-4611-bc39-d62fe42cbd2a.png">

   (_Just focus on the Prompts and that you are connected, exact GUI of yours will be different since I customised mine to not to bleed my eyes_)


## How to share content

It's not enough to just download content - to bring back the DC culture - everyone is encouraged to share their collection as well.<br>
To share folder(s) follow the following steps:

1. Open Eiskalt DC++ & press the following keyboard shortcut to open its __preferences__ window according to your platform
   |Platform|Shortcut|
   |--------|---------|
   |Windows|`ctrl + o`|
   |Linux|`ctrl + o`|
   |MacOS|`cmd + ,`|

2. Now navigate to: `Sharing` > `Basic` and toggle off the `View share in simple mode`.
   <img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223653865-275aba37-f801-4b34-9b41-a6623d3bd44e.png">

3. Now select the folder(s) you want to share.

   > **Note** You will need to click on `down arrows` to expand folders.
  
   > **Warning** You might need to __expand the width of Name column__ to see the names of the folders.

## Some common issues
## Installing mono fonts

This is completely an optional step based on personal preference. If you want to render the ASCII art for `METAHUB` to be rendered properly you will definetly need a mono font.<br>
However there are many options available, for the sake of documenting the exact process we will be installing `hack-nerd-font` which comes with a _mono_ version intself. To install it on your system of preference refer the links below

- [Windows](#installing-font-on-windows)
- [Linux](#installing-font-on-linux)
- [Macos](#installing-font-on-macos)

#### Installing font on Windows
#### Installing font on Linux
#### Installing font on MacOS

- [Install Homebrew](https://brew.sh/) if not already installed.
- Use the following commond to install the `hack-nerd-font`
  ```sh
  brew install font-hack-nerd-font
  ```

***

## Author

- Arpit Bhardwaj ([@proffapt](https://github.com/proffapt))

<p align="center"> Created with lots of <b>&lt;/&gt;</b> and ♥ </p>
