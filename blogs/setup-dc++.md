# Setup DC++ 

1. Download a DC++ Client, I recommend EiskaltDC++ for uniformity across platforms and avoiding confusion.<br>

	#### Windows
	#### Linux
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

2. Open Eiskalt DC++ & press `cmd + ,` key-combination to open its preferences window.

3. Set a `Nick` aka _username_ for your current instance.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223125464-437cbbc0-4e88-46ab-aa5c-a72adf9ba3a8.png">

4. Now Goto `Connection` > `Advanced` > `TLS settings` and choose `Allow TLS`.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223126546-7bbd64fd-e098-4427-91f0-0eaaf80c1ef1.png">

5. In order to render the Welcome message aka `Message of The Day` properly we have to set any mono font for our client.<br>
	To do so Goto `GUI` > `Fonts`, then select any __mono__ font available on your system.<br>
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223131317-2b5329b3-abda-48d3-b1bd-b0f531c4b841.png">

6. Now press `Ok`. 
7. Press `cmd + N`, key-combination for quick connect.<br>
	Enter the current IP for DC++. At the time of writing this blog it is `10.105.12.22`. Press `Ok`.<br>
	<img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/223131882-7e86be2e-d96e-44e3-ad4b-bca4be98b621.png">

8. You should now be connected to the hub and if the fonts are set properly you should see something like this
	<img width="700" alt="image" src="https://user-images.githubusercontent.com/86282911/223134018-c1f1c1f2-4272-4611-bc39-d62fe42cbd2a.png">
