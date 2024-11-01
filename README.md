
![proxmox-dietpi](https://user-images.githubusercontent.com/67932890/213890139-61bd9c23-4ed2-49f2-a627-0b303d0a4f8f.png)

# Proxmox DietPi Installer

A Proxmox Helper Script to install DietPi in Proxmox 8.

## How to Use

There are two ways to install DietPi VM in Proxmox:

1. Use the one-liner installer directly from GitHub.
2. Download the script directly.

All commands should be run in the Proxmox console.

---

### One-liner Installer

Run the following command to install DietPi VM directly from GitHub:

```sh
bash <(curl -sSfL https://raw.githubusercontent.com/dazeb/proxmox-dietpi-installer/main/dietpi-install.sh)
```

---

### Download the Script

You can download the script to your Proxmox host by cloning the repo or using `wget`.

#### Clone the Repository

```sh
git clone https://github.com/dazeb/proxmox-dietpi-installer.git
```

Navigate into the folder, make the file executable, then run the script:

```sh
cd proxmox-dietpi-installer
chmod +x dietpi-install.sh
./dietpi-install.sh
```

#### Download Script Using `wget`

```sh
wget https://raw.githubusercontent.com/dazeb/proxmox-dietpi-installer/main/dietpi-install.sh
```

Make the file executable, then run the script:

```sh
chmod +x dietpi-install.sh
./dietpi-install.sh
```

---

### Installation Prompts

The installer will ask for the following information:

- Where to import the VM disk 
- How much RAM to allocate (default 2GB)
- The number of processor cores (default 2 Cores)

The rest is automatic. Be sure to open the DietPi VM console once the installer finishes and complete the initial startup then you can shutdown and add changes eg, increasing cores, RAM, etc.  

---

### What the Script Does

The `dietpi-install.sh` script performs the following steps:

1. **Prompts for User Input**: Asks for the storage location name.
2. **Installs Required Packages**: Installs `xz-utils` if it is not already installed.
3. **Gets the Next Available VMID**: Retrieves the next available VMID from Proxmox.
4. **Downloads and Decompresses the DietPi Image**: Downloads the specified DietPi image and decompresses it.
5. **Imports the Disk Image**: Imports the decompressed disk image into the specified storage.
6. **Configures the VM**: Sets the VM's CPU cores, RAM, SCSI hardware, network, and disk settings.
7. **Sets VM Metadata**: Sets the VM's name and description.
8. **Starts the VM**: Starts the newly created VM.

## Compatibility

Tested and confirmed working with Proxmox 8.x.

---

## Developers

Developed by Darren Bennett & MichaIng

---

## More Helper Scripts

For more helper scripts like this, check out [tteck's Proxmox Helper Scripts](https://tteck.github.io/Proxmox/)
