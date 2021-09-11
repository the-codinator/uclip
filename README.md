# UClip - The cross device clipboard!

A simple CLI utility tool to copy data across devices, over the internet!

![Shell CLI tool](https://img.shields.io/badge/runtime-bash-blue)
![Development Release Status](https://img.shields.io/badge/release-beta-orange)

## Installation

- Download this file and place it on the system PATH
  - On a unix system, you can run:
    `curl "https://raw.githubusercontent.com/the-codinator/uclip/master/uclip" -o /usr/local/bin/uclip`
  - Alternative you can clone this repo and symlink the script file (`ln -s /usr/local/bin/uclip <path-to-repo>/uclip`)
- Make the actual file executable (`chmod +x /usr/local/bin/uclip`)
- Checkout usage help by running `uclip help`

Runs as a bash shell script & uses cl1p.net online clipboard.

## Available sub-commands:

- `init`: Set up your clipboard id & optionally your encryption key
  - The 'UClip ID' must be URL compatible. It is the unique ID at which your clipboard will be hosted online
  - The 'Encryption Key' is used in the AES 256 crypto algorithm to protect others from reading your data
- `reset`: Clear your stored clipboard id & encryption key
- `write`: Write data from STD-IN to the online clipboard
  - Useful with the pipe operator to copy the output from a command
  - You can paste text directly into the terminal and terminate the input using 'Ctrl + D' (EOF in most shells)
- `push`: Publish text currently on your local clipboard to the online clipboard (i.e. copy from local clipboard and
  paste to online clipboard)
  - Warning: Implemented only for Mac-OS as of now (uses pbcopy)
- `read`: Read data from the online clipboard and output it to STD-OUT
  - Useful to pipe it to another command, or redirect output to a file, or copy to local clipboard using
    clip/xclip/pbcopy
  - Note: reading clears the online clipboard
- `pull`: Populate text currently on the online clipboard to your local clipboard (i.e. copy from online clipboard and
  paste to local clipboard)
  - Warning: Implemented only for Mac-OS as of now (uses pbpaste)
- `version`: Print version

## Working on Windows / Linux

Everything works fine on Windows (via Git Bash / WSL) and Linux, except the local clipboard interactions (pbcopy &
pbpaste). While I've only done some basic testing, here's how I made this work for me on other Operating Systems:

- [Setup pbcopy/pbpaste on Windows for Git Bash & WSL](https://www.techtronic.us/pbcopy-pbpaste-for-wsl/)
- [Setup pbcopy/pbpaste on Linux](https://ostechnix.com/how-to-use-pbcopy-and-pbpaste-commands-on-linux/)

## Additional Features

- Share pastes: At times you may want to copy text to someone else's device (sharing content), but not want to share
  your clipboard id & key. You can temporarily override the account ID & Key using the environment variables `UCLIP_ID`
  & `UCLIP_KEY`. As with the default encryption key, `UCLIP_KEY` is optional.

## Requirements & Dependencies

- An internet connection!
- Shell (something that can run `bash scripts`), so sorry, windows may not work (probably try via `git-bash`?)

This tools runs in the 'bash' environment and requires the following CLI commands for its proper functioning (generally,
these are already available in various shells by default):

- curl: To access the online clipboard
- base64: For encoding text (to deal with special characters)
- openssl: For encrypting data stored on the online clipboard (not used if encryption key is not set)
- pbcopy/pbpaste: For interacting with the local clipboard on Mac-OS

## Disclaimer

This tool uses the free online clipboard service at https://cl1p.net. This tool is not affiliated to it in any way. This
tool uses the online service to power its capabilities. The functionality of this tool is provided 'as-is' and without
any warranty. Authors & copyright holders are not liable for anything. The code for this tool is available for use under
the MIT license.

## Contributing

- Feel free to make pull requests
- Alternatives to this tool are also welcome
- For any issues, please provide re-pro steps (and commit on which the issue is occurring)

## Support

I did this for fun, and it cost me just a few hours, so I don't need anything from anyone for using this. Instead, it
would be awesome if you can support the guys at cl1p.net since we are using their service. You can create a free
account [here](https://cl1p.net/sys/login.jsp) (no email required!), which allows you to see your clip history, store
clips longer, and view access logs, and add password protection. You can support the service by purchasing a premium
(dedicated) URL for as little as $5 a year! The premium features allow you to create dedicated urls, restore previous
settings, even longer retention, and more... Help keep the service alive!
