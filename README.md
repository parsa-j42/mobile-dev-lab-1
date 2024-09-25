# Lab Assignment 1: Spinning Up React Native App

## System Requirements

The system specifications used for the lab were:

- RAM: 16 GB
- CPU: AMD Ryzen™ 7 5700U
- Integrated GPU: Radeon™ Graphics
- Operating System: Linux (Fedora 40 - Workstation Edition)

## Installation Instructions

1. First, install NVM (node version manager) by running:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash 
```

2. Add the nvm loading script to path (~/.zshrc in my case):
```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

3. Run `nvm use 20.17.0` to use the current stable version of Node.js.

4. Run `node -v` to make sure Node.js is on the right version.
## Configuration Steps

To prepare for development builds:

1. Clone Watchman's GitHub repository:

bash
```bash
git clone https://github.com/facebook/watchman.git
```

2. Install Watchman:

bash
```bash
cd watchman

# Ensure Cargo is installed. Either through your OS's package manager or https://rustup.rs/
cargo version
# If not installed, run `sudo dnf install rust cargo`

# Optionally, to save time, you can ask Watchman's build process to install system dependencies
sudo ./install-system-packages.sh

./autogen.sh
```

3. Install OpenJDK runtime environment and development environment:
```bash
sudo dnf install java-latest-openjdk java-latest-openjdk-devel
```

4. Optional Step: If you want to use an emulator, Install Android Studio through either FlatPak, the binary .RPM file provided by the official site, or from JetBrains ToolBox, if you have that installed. Then, use the official Expo guide to configure Android Studio for Emulation through [Expo Environment Setup Guide](https://docs.expo.dev/get-started/set-up-your-environment/?mode=development-build&buildEnv=local&platform=android&device=physical).

5. Plug in your mobile device with a USB cable to the computer, and check if the device is connected by running `adb devices`.

## Project Creation

Run `npx create-expo-app@latest project-name` to create the default pre-populated expo project, with the desired name.

## Running the Project

- Run `npx expo run:android`.
- Alternatively, run `npx expo run:web`.

## Troubleshooting

- If `adb devices` doesn't find your Android device, you may have to enable USB Debugging on your phone (through Developer Options).
- The Watchman Documentation says that there are binary builds available for some Linux distributions, such as Fedora and Debian. However, these docs are outdated, and the new versions of Watchman aren't available prebuilt. They must be built from source, as we've done here.
- If you have trouble building Watchman from source (it can be a tedious and long process sometimes), you can install it threw Homebrew as well.
```bash
# First install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Then install Watchman threw Homebrew
brew install watchman
```
## Resources

- [Watchman Installation Guide](https://facebook.github.io/watchman/docs/install#linux)
- [NVM GitHub Repository](https://github.com/nvm-sh/nvm)
- [Expo Environment Setup Guide](https://docs.expo.dev/get-started/set-up-your-environment/?mode=development-build&buildEnv=local&platform=android&device=physical)