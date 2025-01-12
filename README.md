# Discord Always Rich Presence Fork

## Overview

This fork enables you to display the games you play on your PS4 in Discord Rich Presence at all times. It eliminates the need to have a personal computer running the code continuously by using a cloud-based solution.

---

## How It Works

The original project is available on [zorua98741's GitHub repository](https://github.com/zorua98741/PS4-Rich-Presence-for-Discord). This fork modifies the code to function with a virtual machine (VM) on a public IP that your PS4 can connect to, enabling seamless integration.

---

## Prerequisites

### 1. Cloud VM Setup
- Use a cloud provider such as [Oracle Cloud](https://www.oracle.com/cloud/) or AWS.
- The instance can even be created using a mobile device.
- Follow [this guide](https://medium.com/@Arafatkatze/graphical-user-interface-using-vnc-with-amazon-ec2-instances-549d9c0969c5) to enable a graphical interface for Discord (Discord does not work without it).
- Download Discord from a browser inside the VM.

### 2. Port Forwarding Configuration
- Port forward the required ports for your PS4 to connect to the VM:
  1. Access your router's GUI.
  2. Navigate to the **Port Forwarding Settings**.
  3. Set the **Local IP** to your PS4's static IP (e.g., `192.168.0.21`).
  4. Add the following rules:
     - **Rule 1**:  
       - External and local ports: `2121`  
       - Protocol: `TCP`  
     - **Rule 2**:  
       - External ports: `1` to `64512`  
       - Local ports: `1` to `64512`  
       - Protocol: `TCP/UDP`  

   ⚠️ *Note*: Port forwarding a wide range of ports can be risky. Use this setup cautiously and ensure your network is secure.

### 3. Other Requirements
- A PS4 connected to the same public IP as the VM.
- Basic knowledge of running Python scripts.

---

## Setup Steps

### 1. Copy the Code
- Transfer the `PS4RPD.py` file to your VM.

### 2. Network Configuration
- Ensure no `iptables` rules or subnet settings block your public connection.
- Test the connection using:
  ```bash
  telnet <YOUR_PUBLIC_IP> 2121
  
## 3. Install Dependencies
- Install the required libraries one by one using pip:
  ```bash
  pip install python-dotenv pypresence

### 3.1. Copy and Configure `.env` File
- Copy the `.env.example` file to `.env`:
  ```bash
  sudo mv .env.example .env

- Edit the .env file with your preferred editor (e.g., nano):
    ```bash
    sudo nano .env
    
Replace the placeholder <YOUR_PUBLIC_IP> with the public IP of your VM. Save and exit the editor (for nano, press Ctrl+X, then Y to confirm, and Enter to save).

## 4. Running the Script
- Run the script in the background to keep it running even after you close the terminal:
  ```bash
  nohup python3 PS4RPD.py > output.log 2>&1 &

## 5. Stopping the Script
- If something goes wrong, stop the script by identifying its process and killing it:
  ```bash
  ps aux | grep python3
- then
  ```bash
  kill <PS4RPD.py Process ID>

## Contact
- If you need help, feel free to contact me on Discord: @thedancedewyles.

## Prints 
![image](https://github.com/user-attachments/assets/6760399c-a0ff-4ffc-a501-7f058e80d3cd)
![image](https://github.com/user-attachments/assets/f814dcb9-b54d-4b45-87a0-05fdeb3736c2)



