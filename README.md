# Libero GNU/Linux Build

Welcome to the **Libero GNU/Linux Build** repository! This project provides the build scripts and instructions necessary to build your own Libero GNU/Linux, a lightweight, customizable Linux distribution focused on simplicity, efficiency, and user control.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

## Introduction

Libero GNU/Linux is designed to give users the freedom to create a tailored Linux distribution. Whether you want to build a minimal system, a desktop environment, or a server, Libero GNU/Linux provides the tools to do so with ease.

## Features

- **Modular Build System:** Build only the components you need.
- **Customizable:** Tailor your Linux distribution to your specific needs.
- **Lightweight:** Focus on performance and efficiency.
- **Open Source:** Completely free and open-source.

## Prerequisites

Before you begin, ensure you have the following:

- A Linux-based operating system (Debian/Ubuntu, Arch, Fedora, etc.)
- Basic knowledge of shell scripting and Linux system administration
- Required packages: `bash`, `coreutils`, `gcc`, `make`, `wget`, `curl`, `git`

Run the following script "01Requirements" to know if your host system have all the packages required to build Libero GNU/Linux.

## Getting Started

To get started with building LiberoLinux, follow these steps:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/liberolinux/Build.git
   cd Build
   ```

2. **Install necessary dependencies:**

   Depending on your base system, install the required packages. For example, on Debian/Ubuntu:

   ```bash
   sudo apt-get update
   sudo apt-get install -y build-essential m4 bison yacc wget curl git
   ```

3. **Configure your build:**

   Edit the configuration files in this directory to set up your desired build environment.
   You can set CFLAGS and CXXFlags to your needs despite is not recommended because it can brake the system.

   Edit "DEVICE" variable before running scripts in order to install Libero GNU/Linux on the destination Hard-Drive on the following scripts:

   02Preparation and 10MakingLiberoBootable

5. **Start the build process:**

   Run the build script to start building Libero GNU/Linux:

   ```bash
   ./02Preparation
   ```

   The script will download, compile, and install the selected components based on your configuration.
   Then, after 02Preparation script, run the following scripts by numeric order, next one "03CrossCompiler" and so on.

## Network Configuration

After Building and boot into Libero GNU/Linux and you need to configure Network, it is advisable to read Chapter 9.2 from Linux From Scratch Book.
Here's a snippet:

The command below creates a basic configuration file for an IPv4 DHCP setup:

```bash
cat > /etc/systemd/network/10-eth-dhcp.network << "EOF"
[Match]
Name=<network-device-name>
[Network]
DHCP=ipv4
[DHCPv4]
UseDomains=true
EOF
```

For Static IP Address you can edit the following file:

```bash
cat > /etc/systemd/network/10-eth-static.network << "EOF"
[Match]
Name=<network-device-name>
[Network]
Address=192.168.0.2/24
Gateway=192.168.0.1
DNS=192.168.0.1
Domains=<Your Domain Name>
EOF
```

## Usage

After building, you can:

- **Install the system** to a new partition or disk.
- **Create a bootable ISO** for distribution or personal use.
- **Customize further** by modifying the build scripts and configuration files.

## Contributing

We welcome contributions from the community! If you'd like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add some feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.

Please make sure your code adheres to our coding standards and includes appropriate tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Support

If you encounter any issues or have questions, feel free to open an issue in the repository or contact us through the [Libero GNU/Linux Community Forums](https://libero.eu.org/community).
