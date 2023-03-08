[^1]: [Which campus has highest total share and users on DC++ in India?](https://www.quora.com/Which-campus-has-highest-total-share-and-users-on-DC++-in-India). Quora. Retrieved May 1, 2015.

# DC++

IIT Kharagpur __once had__ one of the largest DC ([Direct Connect](https://en.wikipedia.org/wiki/Advanced_Direct_Connect)) networks in India[^1]. It lost its glory when the pendamic hit and everything went online. This is an effort to restore that glory back, by educating students about "_How can one connect to the DC Hub properly_". Following is the structure of this documentation for a quick overview and easy navigation.

- [Installing the client](#installing-the-client)
  - [Windows](#windows)
  - [Linux](#linux)
  - [MacOS](#macos)
- [Configuring the client](#configuring-the-client)
- [How to share content](#how-to-share-content)
- [How to download content](#how-to-download-content)
- [Some common issues](#some-common-issues)
- [Installing mono fonts](#installing-mono-fonts)
  - [Windows](#installing-font-on-windows)
  - [Linux](#installing-font-on-linux)
  - [Macos](#installing-font-on-macos)

## Installing the client

The IITKGP DC Hub is a private hub and inaccessible from outside the IIT Kharagpur's network. Users connect to hubs using DC clients, and are able to share files with each other at high speeds. The most popular hub is [HiT Hi FiT Hai](https://wiki.metakgp.org/w/HiT_Hi_FiT_Hai).<br>
There are various DC clients available for different platforms. To name a few, we have<br>
|Platforns|Client(s)|
|---------|---------|
|Windows|[EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/Windows/EiskaltDC%2B%2B-2.4.2-x86_64-installer.exe/download), [DC++](https://dcplusplus.sourceforge.io/)|
|Linux|[EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/Linux/), [LinuxDC++](https://linux.softpedia.com/get/Communications/Filesharing/LinuxDCplusplus-16399.shtml), [ncdc](https://dev.yorhel.nl/ncdc)|
|MacOS|[EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/macOS/EiskaltDC%2B%2B-2.4.2-x86_64.dmg/download), [Shakespeer](https://sourceforge.net/projects/shakespeer/), [ncdc](https://saiankit.medium.com/how-to-use-dc-on-mac-using-ncdc-50bcc78aad01)|
   
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
	
	> **Note** If you don't have any `mono` font installed on your system then refer to the section [Installing mono fonts](#installing-mono-fonts) for installing one, based on your platform

6. Now press `Ok`. 

7. Press the following key combination for quick connect dialog box, according to your platform.<br>
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

> **Warning** It is a must to mirror whatever you download, so you atleast have to share the folder in which you download content from the HUB.

1. Open Eiskalt DC++ & press the following keyboard shortcut to open its __preferences__ window according to your platform
   |Platform|Shortcut|
   |--------|---------|
   |Windows|`ctrl + o`|
   |Linux|`ctrl + o`|
   |MacOS|`cmd + ,`|

2. Now navigate to: `Sharing` > `Basic` and toggle off the `View share in simple mode`.
   <img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223653865-275aba37-f801-4b34-9b41-a6623d3bd44e.png">

3. Now select the folder(s) you want to share. Keep the following things in mind:
   - You will need to click on `down arrows` to expand folders.
   - You might need to __increase the width of Name column__ to be able to see names of the folders.

## How to download content

1. `Right click` on the user you want to browse files for and select `Browse Files`.<br>
   <img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/223689275-e472a0d7-72ab-437e-be6f-402184bacd47.png">

2. Now you will be taken to the file explorer for the user's shared directory. Use the `Down Arrow` to expand the folders of your interest.
3. Now `Right click` on the file you want to download and select `Download` or `Download to` (for a list of frequently used folders to download).<br>
   <img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223690165-a7b398a7-ebd9-4ea6-ae22-3cc71ba4de62.png">
   
4. Now enjoy tremendously fast download speed and the file will be downloaded.

> **Note** Don't forget to mirror the content you download.

## Some common issues

1. You are connected to the hub and can also see the list of all connected users but when you try to browse the files for any user it keeps on connecting and finally nothing happens. This might be a result of multiple configurational and system issues. To fix them you are recommeded to follow the below practices:

  - Allow all incoming connections for the client through your firewall - recommended for all platforms.
  - Always use the client in `Active mode`.<br>
    To do so, Goto: `Preferences` > `Connection` > `Connection` then select `Active Mode` and restart the client.<BR>
    <img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223679604-5e05c4df-e0e0-4cfb-b6c1-e4c688e3ebc7.png">
  - Make sure you meet the minimum sharing requirement to be able to browse and download content from other users.<br> 
    Refer to the rules for the exact number. At the time of writing this documentation, the rules are:<br>
    <img width="400" alt="image" src="https://user-images.githubusercontent.com/86282911/223686051-32cd9e9c-adfd-4911-ab60-0d668f6bdd41.png">

2. Nick already taken by another user, even if your nick was unique.<br>
   <img width="500" alt="image" src="https://user-images.githubusercontent.com/86282911/223686661-ff00172a-2da2-47b2-8836-b77c4671d553.png">
	
   This happens when the connection with the hub is dropped abruptly. It can be due to multiple reasons like:
	- Network was turned of abruptly.
	- Network was changed abruptly.
	
   Due to which the connection packets remain alive and it appears to the hub that you are still connected, i.e., your previous connection wasn't closed properly.<br>
   `FIX:` The only way to fix it is wait for at max 15 minutes so that the packets expire automatically and then you can connect to the hub normally. Usually they expire quite early but sometimes might take time so better have a walk outside you room, get some fresh air then try to connect to the hub again.

## Installing mono fonts

This is completely an optional step based on personal preference. If you want to render the ASCII art for `METAHUB` to be rendered properly you will definetly need a mono font.<br>
However there are many options available, for the sake of documenting the exact process we will be installing `hack-nerd-font` which comes with a _mono_ version of itself. To install it on your system of preference refer the links below

- [Windows](#installing-font-on-windows)
- [Linux](#installing-font-on-linux)
- [Macos](#installing-font-on-macos)

#### Installing font on Windows

1. Download a [Nerd Font](http://nerdfonts.com/) - recommended [Hack Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.3.3/Hack.zip).
2. Extract the downloaded zip file.
3. To install all of them simultaneously, you first need to select them all. To do so, click the first font on the list, hold the `Shift` key, and click the last font. You can also drag to select them if you want. As long as they’re all selected, it doesn’t matter how you do it. It should look like this.:<br>
   <img width="600" alt="image" src="https://user-images.githubusercontent.com/86282911/223692778-637da01b-03ba-4e26-83d2-085d6ca0c4f6.png">

4. Next, `right-click` on the name of any of the font files. If you have multiple user accounts on your PC, you might want to click `Install for All Users`. Otherwise, just click `Install`.<br>
   <img width="600" alt="image" src="https://user-images.githubusercontent.com/86282911/223693099-98f7f279-4540-470a-8d17-0bbe3a219f07.png">

5. If you already installed some of the fonts, you’ll get a popup warning you about it. Click `Yes` and let it proceed.
   <img width="350" alt="image" src="https://user-images.githubusercontent.com/86282911/223693473-433f1958-ffe4-4768-8c11-9f54fefd06a6.png">

6. Another window will indicate the progress of the installation. Once it disappears, your fonts are installed and ready for use.
	
#### Installing font on Linux

1. Download a [Nerd Font](http://nerdfonts.com/) - recommended [Hack Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.3.3/Hack.zip).
2. Unzip and copy to `~/.fonts`.
3. Run the following command to manually rebuild the font cache.
   ```sh
   fc-cache -fv
   ```

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
