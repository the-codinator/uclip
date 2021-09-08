# UClip - The cross device clipboard!

A simple CLI utility tool to copy data across devices, over the internet!

## Installation

- Download this file and place it on the system PATH
  - Make sure this file's name is "uclip", else all commands need to use the actual file name instead
  - Alternative you can clone this repo and symlink (`ln -s /usr/bin/uclip <absolute-path-to-uclip>`)
- Make the actual file executable (`chmod +x uclip`)
- Checkout usage help by running `uclip help`

Code license: MIT
Uses cl1p.net online clipboard
Runs using Bash. Needs CLIs: curl, base64, openssl (optional, for encryption feature), pbcopy/pbpaste (Mac OS features)

## Available sub-commands:

- `login`: Setup your clipboard id & optionally your encryption key
  - The 'UClip ID' must be URL compatible. It is the unique ID at which your clipboard will be hosted online
  - The 'Encryption Key' is used in the AES 256 crypto algorithm to protect others from reading your data
- `logout`: Clear your stored clipboard id & encryption key
- `write`: Write data from STD-IN to the online clipboard
  - Useful with the pipe operator to copy the output from a command
  - You can paste text directly into the terminal and terminate the input using 'Ctrl + D' (EOF in most shells)
- `push`: Publish text currently on your local clipboard to the online clipboard (i.e. copy from local clipboard and paste to online clipboard)
  - Warning: Implemented only for MAC OS as of now (uses pbcopy)
- `read`: Read data from the online clipboard and output it to STD-OUT
  - Useful to pipe it to another command, or redirect output to a file, or copy to local clipboard using clip/xclip/pbcopy
  - Note: reading clears the online clipboard
- `pull`: Populate text currently on the online clipboard to your local clipboard (i.e. copy from online clipboard and paste to local clipboard)
  - Warning: Implemented only for MAC OS as of now (uses pbpaste)
  
## Additional Features

- Share pastes: At times you may want to copy text to someone else's device (sharing content), but not want to share your clipboard id & key.
  You can temporarily override the account ID & Key using the environment variables `UCLIP_ID` & `UCLIP_KEY`.
  As with the default encryption key, `UCLIP_KEY` is optional.

## Dependencies

This tools runs in the 'bash' environment and requires the following CLI commands for its proper functioning

- curl: To access the online clipboard
- base64: For encoding text (to deal with special characters)
- openssl: For encrypting data stored on the online clipboard (not used if encryption key is not set)
- pbcopy/pbpaste: For interacting with the local clipboard on MAC OS

## Disclaimer

This tool uses the free online clipboard service at https://cl1p.net.
This tool is not affiliated to it in any way. This tool uses the online service to power its capabilities.
The functionality of this tool is provided 'as-is' and without any warranty.
Authors & copyright holders are not liable for anything. The code for this tool is available for use under the MIT license.

## Contributing

- Feel free to make pull requests
- Alternatives to this tool are also welcome
- 
