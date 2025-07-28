# 🌐 IIS Web Server Setup Guide on Windows 11 Pro

## ✅ What is IIS?

**Internet Information Services (IIS)** is a flexible, secure, and manageable web server developed by Microsoft.  
It supports HTTP, HTTPS, FTP, FTPS, and more, and is often used to host websites and web applications on Windows.

---

## 🧰 Prerequisites

- Windows 11 Pro installed  
- Administrator privileges

---

## 🛠️ Step-by-Step Installation

### 1. Open Windows Features

- Press `Windows + S` and type: **"Windows Features"**
- Click **“Turn Windows features on or off”**

### 2. Enable IIS

- In the Windows Features dialog:
  - ✅ Check **Internet Information Services**
  - *(Optional)* Expand it and check:
    - **Web Management Tools**
    - **World Wide Web Services** > **Application Development Features** (e.g., ASP.NET, CGI)
- Click **OK**

### 3. Wait for Installation

- Windows will apply the required changes.
- Restart your PC if prompted.

---

## 🚀 Launching IIS Web Server

### 1. Open IIS Manager

- Press `Windows + S`, type **“IIS”**
- Open **"Internet Information Services (IIS) Manager"**

### 2. Test the Server

- Open your browser and navigate to:  
  `http://localhost`
- You should see the **default IIS welcome page**.

---

## 📁 Deploying a Website

### 1. Add a New Website

- In **IIS Manager**:
  - Right-click **“Sites”** > **Add Website…**
  - **Site name**: `MyWebsite`  
  - **Physical path**: e.g., `C:\inetpub\mywebsite`  
  - **Port**: `80` or any other available port
  - Click **OK**

### 2. Grant Permissions

- Ensure the `IIS_IUSRS` group has access:
  - Right-click your site folder > Properties > Security tab  
  - Add **Read/Execute** permissions for `IIS_IUSRS`

---

## 🔐 (Optional) Enabling HTTPS (SSL)

1. Purchase or generate an SSL certificate  
2. Import the certificate:
   - Go to **Server node** > **Server Certificates** > **Import**
3. Bind your site to HTTPS:
   - Select your site > **Bindings** > **Add** > Type: HTTPS > Select certificate

---

## ⚠️ Troubleshooting Tips

- **Port 80 busy?**
  - Use another port or stop conflicting apps (e.g., Skype)
  - Run:  
    ```cmd
    netstat -ano | findstr :80
    ```
- **Changes not showing?**
  - Clear browser cache or restart the site in IIS

---

## 📎 Useful PowerShell Commands

Install IIS:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-WebServerRole -All
