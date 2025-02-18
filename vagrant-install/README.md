# Vagrant Installation Script

This script installs Vagrant by adding the HashiCorp repository to your system, downloading the GPG key, and installing Vagrant using `apt` on a Debian-based system.

## Prerequisites

- A Debian-based Linux distribution (e.g., Ubuntu).
- sudo privileges on the system.

## Installation Instructions

1. **Download the script:**

   Create a new file named `install_vagrant.sh` and paste the following content:

   ```bash
   #!/bin/bash

   # Fetch and dearmor HashiCorp GPG key
   wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

   # Add HashiCorp apt repository
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

   # Update package list and install Vagrant
   sudo apt update && sudo apt install -y vagrant
   ```
## Reference

For more information, you can refer to the official Vagrant installation guide: [Vagrant Installation - HashiCorp](https://developer.hashicorp.com/vagrant/install)
