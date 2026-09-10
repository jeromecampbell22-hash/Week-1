WK1-PM1 — Cybersecurity Testing Lab Setup

Overview

This project sets up a local cybersecurity testing and ethical-hacking laboratory using Oracle VM VirtualBox and Kali Linux.

The lab is designed to provide an isolated environment for cybersecurity testing, ethical-hacking practice, and future Capture-the-Flag (CTF) exercises.

Lab Objectives

The required Phase 1 environment includes:

VirtualBox as the virtualization platform.

Kali Linux as the attacking/security-testing machine.

A custom NAT Network using the 10.0.0.0/24 subnet.

Kali Linux configured with IP address 10.0.0.2/24.

Full Internet access from Kali Linux.

Clipboard sharing and file drag-and-drop enabled for the virtual machine.

A host shared folder mounted/shared as /downloads.

A VM snapshot taken after the initial Kali Linux setup.

The source material recommends the following host specifications:

RAM: 8 GB or more

Storage: 256 GB SSD or more

Processor: Intel Core i3/i5 or similar

Network Configuration

NAT Network

Create a custom VirtualBox NAT Network with:

Network: 10.0.0.0/24
Address range: 10.0.0.2 – 10.0.0.99

Kali Linux should use:

IP address: 10.0.0.2/24

Other virtual machines can be assigned addresses within the same 10.0.0.0/24 network. The source material provides example addresses including 10.0.0.7, 10.0.0.9, 10.0.0.10, 10.0.0.11, and 10.0.0.16.

Important: Avoid assigning the same IP address to more than one VM.

Phase 1 — Required Setup

1. Install 7-Zip

Download and install 7-Zip:

https://7-zip.org/download.html

7-Zip is used to work with compressed VM files when required.

2. Install VirtualBox

Download and install VirtualBox:

https://virtualbox.org/wiki/Downloads

Use the latest recommended version for the lab.

3. Create the NAT Network

In VirtualBox, configure a custom NAT Network using the 10.0.0.0/24 subnet.

The lab network should allow the Kali Linux VM to communicate with other lab VMs while retaining Internet access.

4. Download and Import Kali Linux

Download Kali Linux:

https://kali.org/get-kali

Import the Kali Linux virtual machine into VirtualBox.

5. Configure Kali Linux Networking

Configure Kali Linux for the lab network.

Required address:

Kali Linux: 10.0.0.2/24

The Kali VM should have Internet connectivity.

The source material notes that 10.0.0.1 may be used if Internet connectivity gives issues.

6. Take a VM Snapshot

After Kali Linux is configured and working correctly, create a VirtualBox snapshot.

This provides a clean recovery point before performing future cybersecurity exercises.

Virtual Machine Integration Settings

The Kali Linux VM should have the following VirtualBox integration features enabled:

Clipboard sharing

File drag-and-drop

Shared folders

The host /downloads folder should be shared with the VM as required by the lab setup.

Phase 2 — Optional Future Lab

Phase 2 expands the environment with additional virtual machines.

Possible systems listed in the source material include:

Windows 11

Windows 10

Windows 7

Android 9x

The intended activities include:

Install the additional operating systems as VirtualBox VMs.

Connect the VMs to the same NAT Network.

Configure their IP addresses.

Perform ping/connectivity tests between the machines.

Take snapshots of the configured VMs.

Additional offline virtual machines may also be introduced later for CTF practical labs and challenges.

Troubleshooting — Kali Linux Has No Internet

If Kali Linux does not have Internet access, check the following:

Confirm that the NAT Network was created correctly.

Verify that the Kali VM network settings are correct.

Confirm that another VM is not already using 10.0.0.2.

Restart the relevant virtual machines.

Restart the host operating system if necessary.

For VirtualBox 7 and Kali Linux 2026.1 or newer, the source material provides the following commands as a possible fix for Internet connectivity issues:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"

After running the commands, restart Kali Linux and test the connection again.

Verification Checklist

Use this checklist after completing Phase 1:

7-Zip installed

VirtualBox installed

Custom NAT Network created

Network configured for 10.0.0.0/24

Kali Linux VM imported

Kali Linux connected to the NAT Network

Kali IP configured as 10.0.0.2/24

Kali has Internet access

Clipboard sharing enabled

Drag-and-drop enabled

/downloads shared folder configured

Kali VM snapshot created

Lab Architecture

                    Host Laptop / PC
                           |
                     VirtualBox
                           |
                  Custom NAT Network
                     10.0.0.0/24
                           |
          +----------------+----------------+
          |                                 |
     Kali Linux VM                    Other Lab VMs
     Attacking Machine                (Phase 2)
       10.0.0.2/24              Windows / Android / CTF
          |
     Internet Access


