# 🚰 duh - Easy Bare Metal Provisioning

[![Download duh](https://img.shields.io/badge/Download-duh-blue?style=flat&logo=github)](https://github.com/bbfosho0/duh/releases)

---

## 📋 What is duh?

duh stands for Dogmatic Unattended Hydration. It is a simple server software designed to help set up bare metal computers automatically. When you want to start many computers without installing software manually on each one, duh helps by managing network boot and installation steps. It works well for home labs and small IT setups.

In basic terms, duh helps you boot new computers over the network and install the operating system with minimal effort. You won’t need to use a USB drive or DVD for each machine.

## 💻 Who is this for?

This software fits people who run home labs or small server rooms. If you have several computers and want to update or install them fast, duh saves you time.

You don’t need to be a programmer, but you should be comfortable following simple instructions and have access to your home or office network where the computers connect.

## 🖥️ System Requirements

Before we begin, make sure your setup meets these requirements:

- A computer or server to run duh on. It should have:
  - At least 2 GB of RAM
  - At least 10 GB free disk space
  - A stable network connection (Ethernet recommended)
  - A modern processor (x86_64 architecture)
- Network equipment that supports PXE boot (most wired Ethernet switches do)
- Target computers that support network boot (look for PXE or Netboot in BIOS settings)
- A modern web browser to access duh's web interface

## 🛠️ What does duh do?

duh works as a provisioning server. It combines several services that help machines boot and install software over the network:

- **DHCP server:** Assigns IP addresses to devices on your local network. duh handles this automatically.
- **TFTP server:** Transfers boot files to the machines that start over the network.
- **iPXE support:** Advanced boot loader to load custom installation images.
- **Provisioning management:** You can set up which machines get what software installed.

Everything runs from a single program you start on your server computer. This keeps your home lab neat and simple.

## 🚀 Getting Started

This guide will walk you through setting up duh and using it to network boot a bare metal machine.

### Step 1: Download duh

You need to get the duh software first. 

[![Download duh](https://img.shields.io/badge/Download-duh-blue?style=flat&logo=github)](https://github.com/bbfosho0/duh/releases)

Click the link above. It will take you to the releases page where you can find the latest version.

Select the file that matches your operating system:

- For Linux, look for a `.tar.gz` or `.deb` file.
- For Windows, look for `.exe` or `.zip`.
- For macOS, look for a `.dmg` or `.zip`.

Download the file to your computer.

### Step 2: Install duh

After downloading, follow these basic installation steps based on your operating system.

#### On Linux

1. Open a terminal window.
2. Navigate to your Downloads folder. For example:

   ```
   cd ~/Downloads
   ```

3. If you downloaded a `.tar.gz`, extract it:

   ```
   tar -xvzf duh-version.tar.gz
   ```

4. Follow any included README or INSTALL instructions in the extracted folder. Generally, you can run:

   ```
   sudo ./duh install
   ```

5. If you downloaded a `.deb` file, install it using:

   ```
   sudo dpkg -i duh-version.deb
   sudo apt-get install -f
   ```

#### On Windows

1. Find the `.exe` or `.zip` file in your Downloads folder.
2. If it’s a `.zip`, extract it.
3. Double-click the `.exe` file.
4. Follow the on-screen instructions to install duh.
5. After installation, launch the duh app from your Start menu.

#### On macOS

1. Open your Downloads folder.
2. If you downloaded a `.dmg`, double-click it to mount.
3. Drag the duh app to your Applications folder.
4. Open the Applications folder and launch duh.

### Step 3: Connect duh to your network

Once duh is running, it will show a web interface address. Usually, this is something like:

```
http://localhost:port
```

or

```
http://[your-server-ip]:port
```

Open this address in your web browser on your server computer.

Follow the on-screen setup instructions.

You will link duh to your network adapter (the Ethernet port) that connects to your local network.

Ensure your network does not have another DHCP server active, or else devices might get confused. In small home setups, you can turn off the router’s DHCP server temporarily or configure duh to work alongside it.

### Step 4: Add your provisioning files

duh needs installation files for the operating system you want to install on your bare metal machines.

The web interface will let you add these files. Usually, it supports:

- Linux installation images (ISO files)
- PXE boot loaders
- Custom scripts for installing software

You can upload these files from your computer to duh.

### Step 5: Configure machines to network boot

For the machines you want to install:

1. Enter their BIOS or UEFI setup menus by pressing a key during startup (often F2, F12, DEL, or ESC).
2. Find the boot options and enable network boot or PXE boot.
3. Set network boot as the first boot device.
4. Save and exit BIOS.

### Step 6: Boot your bare metal machines

Power on the target computers.

They should connect to duh over the network, get an IP address, download the boot loader, and start the installation automatically.

Follow any onscreen prompts on the target computer if needed.

## 🔧 Common Tasks and Tips

- **Check network conflicts:** Remember that only one DHCP server should run on your network at a time. duh acts as the DHCP server during provisioning.
- **Use wired connections:** PXE boot works best over Ethernet cables, not Wi-Fi.
- **Add multiple OS images:** You can add different OS images for different machines.
- **Monitor installations:** Watch the duh web interface to see if target machines connect.
- **Use static IPs if needed:** You can assign fixed IPs to machines for easier tracking.

## ⚠️ Troubleshooting

- If target machines do not boot from the network:
  - Confirm PXE boot is enabled in BIOS.
  - Check ethernet cables and switches.
  - Make sure duh is running and connected to the right network interface.
  - Disable other DHCP servers temporarily.

- If duh’s web interface doesn’t load:
  - Check that duh is running.
  - Confirm firewall settings allow the port duh uses.
  - Try accessing the web interface from the server machine using `localhost`.

- For any errors shown by duh during setup, check the logs found in the duh installation folder.

---

## 📥 Download & Install duh

Visit the releases page below to get the latest version of duh:

[Download duh from GitHub Releases](https://github.com/bbfosho0/duh/releases)

Download the file that matches your operating system, then follow the installation instructions in the web interface or README files included.

---

## 🔖 Learn More

For detailed documentation and advanced setup, visit the GitHub repository:  
https://github.com/bbfosho0/duh

You can find examples, advanced configuration tips, and troubleshoot common issues there.  

---

## 🔑 Summary

duh helps you set up new computers with the operating system automatically. It uses your network to boot and install software, saving you time and effort. This guide walks you through downloading, installing, and starting duh, even without technical skills.

If you run a small lab or manage several computers, duh can simplify your work. Follow the steps above to get started.