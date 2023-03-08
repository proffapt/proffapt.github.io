[^1]: [Which campus has highest total share and users on DC++ in India?](https://www.quora.com/Which-campus-has-highest-total-share-and-users-on-DC++-in-India). Quora. Retrieved May 1, 2015.

# Setup DC++ 

IIT Kharagpur had one of the largest DC ([Direct Connect](https://en.wikipedia.org/wiki/Advanced_Direct_Connect)) networks in India[^1]. It lost it's glory when the pendamic and everything went online. Users connect to hubs using DC clients, and are able to share files with each other at high speeds. The most popular hub is HiT Hi FiT Hai. 

1. Download a DC++ Client, I recommend EiskaltDC++ for uniformity across platforms and avoiding confusion.<br>

   #### Windows
   [Download Eiskalt DC++](https://sourceforge.net/projects/eiskaltdcpp/files/Windows/).<br>
   Go through the basic installation setup and install it.


   #### Linux

   Install dcpp on debian based
   ```sh
   sudo apt install eiskaltdcpp
   ```

    #### MacOS
	
    [Install Homebrew](https://brew.sh/) - _skip this step if already present_.
	- To check whether it is installed or not, use the following command
	  ```sh
	  command -v brew
	  ```

	- If the output is like follwoing, then brew is installed!
   	  ```sh
	  ~> command -v brew
	  /opt/homebrew/bin/brew
	  ```
 
     Install Eiskalt DC++ using the following command
     ```sh
     brew install eiskaltdcpp
     ```

2. Open Eiskalt DC++ & press the following key combinations to open its preferences window, according to your platform

   |Platform| Keycombination|
   |--------|---------|
   | Windows| CTRL + O|
   |Linux|CTRL + O|
   |MacOS | CMD + , |

3. Set a `Nick` aka _username_ for your current instance. __It must be unique__.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223125464-437cbbc0-4e88-46ab-aa5c-a72adf9ba3a8.png">

4. Now Goto: `Connection` > `Advanced` > `TLS settings` and choose `Allow TLS`.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223126546-7bbd64fd-e098-4427-91f0-0eaaf80c1ef1.png">

5. In order to render the _welcome message_ aka `Message of The Day` properly you need to set any mono font for the client.<br>
	To do so Goto: `GUI` > `Fonts`, then select any __mono__ font available on your system.<br>
	You will need to double click on the fonts to change them.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223131317-2b5329b3-abda-48d3-b1bd-b0f531c4b841.png">
	
	> **Note** If you don't have any `mono` font installed on your system then refer to the section for installing one based on your platform

6. Now press `Ok`. 

7. Press the following key combination for quick connect, according to your platform.<br>
   |Platform| Keycombination|
   |--------|---------|
   | Windows| CTRL + N|
   |Linux|CTRL + N|
   |MacOS | CMD + N |

   Enter the current IP for DC++. At the time of writing this blog it is `10.105.12.22`. Press `Ok`.<br>
	<img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/223131882-7e86be2e-d96e-44e3-ad4b-bca4be98b621.png">

8. You should now be connected to the hub and if the fonts are set properly you should see something like this. <br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223134018-c1f1c1f2-4272-4611-bc39-d62fe42cbd2a.png">

   (_Just focus on the Prompts and that you are connected, exact GUI of yours will be different since I customised mine to not to bleed my eyes_)


## How to share content

<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223491318-fd8db15a-04ed-464a-8c8f-69b4650087d1.png">

## Installing the required fonts
