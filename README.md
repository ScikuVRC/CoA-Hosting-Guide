# How to Host a CoA Server for Your Friends

### Simple Setup & Configuration Guide

This guide will walk you through setting up a **CoA server** for either **local/LAN play** or **online play with friends**.

> **Difficulty:** Beginner
> **Platform:** Windows
> **Recommended:** Notepad++ and HeidiSQL

---

## 1. Server Installation, Update & Database Setup

### Step 1 — Download the Required Files

1. Download the **CoA Repack** and the latest **CoA Repack Update** from `#js-3067`.
2. Create a new folder anywhere on your computer.
3. Name the folder something simple, such as:

```text
Server
```

4. Extract the **CoA Repack** into this folder.
5. Extract the **CoA Repack Update** directly into the **root of your Server folder**.

Your folder structure should look similar to:

```text
Server
├── CoA-Repack
├── CoA Repack Update
├── Start_All_Server.bat
├── Stop_All_Server.bat
└── ...
```

### Step 2 — Create the Database

1. Run:

```text
Start_All_Server.bat
```

2. Allow the server components to start and create the required databases.
3. Check the console windows for errors.
4. If everything starts without errors, run:

```text
Stop_All_Server.bat
```

### Step 3 — Apply the Update

1. Open the **CoA Repack Update** folder.
2. Run:

```text
Apply_Update.bat
```

3. Wait for the update process to complete.
4. If the installation finishes successfully without errors, you're ready to configure the server.

---

# 2. Configure the Server

You can configure the server for either **local/LAN play** or **online play**.

## Local / LAN Server

If you're only planning to play locally, you can leave the server bound to:

```text
127.0.0.1
```

Do not change the BindIP setting.

## Online Server

If you want friends outside your network to connect, change the server's bind address to:

```text
0.0.0.0
```

### Step 1 — Configure Authserver

Navigate to:

```text
Server → CoA-Repack → Settings
```

Open:

```text
Authserver.conf.template
```

Find:

```text
BindIP =
```

For an online server, set it to:

```text
BindIP = "0.0.0.0"
```

### Step 2 — Configure Worldserver

In the same **Settings** folder, open:

```text
Worldserver.conf.template
```

Find:

```text
BindIP =
```

Set it to:

```text
BindIP = "0.0.0.0"
```

Save both files.

---

# 3. Configure the Realmlist

Next, you'll need to tell the server what address your friends should use to connect.

### Step 1 — Open Manage.py

Navigate to:

```text
Server → CoA-Repack → Scripts
```

Open:

```text
Manage.py
```

You can use **Notepad** or, preferably, **Notepad++**.

Press:

```text
CTRL + F
```

Search for:

```text
mysql(f"UPDATE acore_auth.realmlist SET
```

You should find the section that configures the realm's **Name** and **Address**.

### Step 2 — Change the Realm Name

Change:

```text
Name=
```

to whatever name you want your server to appear as.

For example:

```text
Name=My CoA Server
```

### Step 3 — Set the Server Address

Change:

```text
Address=
```

to your **public IPv4 address** if you're hosting the server online.

If you don't know your public IPv4 address, you can check it here:

[WhatIsMyIPAddress](https://whatismyipaddress.com/?utm_source=chatgpt.com)

> **Important:** Your public IP is the address your friends use to reach your server from outside your home network. You may also need to configure your router/firewall to allow the server's required ports.

Save `Manage.py` when finished.

---

# 4. Start the Server

Once you've completed the configuration:

1. Run:

```text
Start_All_Server.bat
```

2. Watch the server consoles for errors.
3. If everything starts successfully, your CoA server should now be running.

🎉 **Congratulations! Your server is ready.**

Your friends can now connect using the realm/server address you configured.

---

# 5. Optional — SQL Database Management

If you want to manually manage your server's SQL databases, you can use a program such as **HeidiSQL**.

### Step 1 — Find the Database Credentials

Navigate to:

```text
Server → Settings
```

Open:

```text
authserver.conf
```

Search for:

```text
LoginDatabaseInfo =
```

The default credentials should contain:

```text
User: acore
Password: 388f3dea4cc08d5f505188fcb3f357145808356084d0a627
```

### Step 2 — If HeidiSQL Cannot Connect

Open:

```text
Server → Settings → authserver.conf.template
```

Go to approximately **line 232** and find:

```text
LoginDatabaseInfo =
```

Change it to:

```text
LoginDatabaseInfo = "127.0.0.1;3307;acore;388f3dea4cc08d5f505188fcb3f357145808356084d0a627;acore_auth"
```

Save the file and try connecting again through HeidiSQL.

> **Important:** Make sure `MySQL.bat` is running before attempting to connect to the database.

---

# 6. Optional — Installing CoA Bots

If you want to add bots to your server:

### Step 1 — Download CoA Bots

Download the **CoA Bots** package:

[CoA Bots Download](https://drive.proton.me/urls/YFJWS1QVHR?utm_source=chatgpt.com#iVsuYKfzuNYe)

### Step 2 — Extract the Files

Extract the **entire CoA Bots folder** into your server's **root directory**.

### Step 3 — Run the Installer

Run:

```text
Installer-Bots.bat
```

Allow the installation to complete.

### Step 4 — Start the Server

Run:

```text
Start_All_Server.bat
```

Check the server consoles for errors.

If everything starts normally, the bots should now be installed and ready to use.

---

# ✅ Quick Setup Checklist

Before inviting your friends, make sure you've completed the following:

* [ ] CoA Repack downloaded
* [ ] CoA Repack extracted
* [ ] CoA Repack Update extracted
* [ ] `Start_All_Server.bat` successfully run
* [ ] `Apply_Update.bat` successfully completed
* [ ] `Authserver.conf.template` configured
* [ ] `Worldserver.conf.template` configured
* [ ] `BindIP` set to `0.0.0.0` for online hosting
* [ ] Realm name configured
* [ ] Public IPv4 configured
* [ ] Server starts without errors
* [ ] Router/firewall configured if required
* [ ] Optional SQL tools configured
* [ ] Optional CoA Bots installed

## 🎮 You're Ready to Play!

Once the server starts successfully, give your friends the appropriate connection information and have them connect to your realm.

**For LAN:** Use your local network IP.

**For Internet play:** Use your public IPv4 address and ensure the necessary ports are forwarded/allowed through your router and firewall.

