
## Syncthing Configuration Guide
# Add a Remote Device and Share a Folder

* **After installing Syncthing**, perform the following steps to add the remote device and configure the folder to be synchronized.

# Prerequisites

Before you begin, ensure that:

- Syncthing is installed on both the local and remote systems.
    
- Both Syncthing instances are running.
    
- You can access the Syncthing Web GUI on both devices.
    
- You have the **Device ID** of the remote system.
    

---

# Step 1: Open the Syncthing Web Interface

Open a web browser and access the Syncthing Web GUI.

Example:

```
http://localhost:8384
```

or

```
http://<Server-IP>:8384
```

---

# Step 2: Obtain the Remote Device ID

On the remote server:

1. Open the Syncthing Web GUI.
    
2. Click **Actions** → **Show ID**.
    
3. Copy the displayed **Device ID**.
    

The Device ID is a unique identifier used to securely connect Syncthing devices.

---

# Step 3: Add the Remote Device

On the local machine:

1. Click **Add Remote Device**.
    
2. In the **Device ID** field, paste the copied Device ID.
    
3. Enter a friendly **Device Name** (for example, `Remote-Server`).
    
4. Leave the default settings unless your environment requires changes.
    
5. Click **Save**.
    

---

# Step 4: Accept the Device Request

On the remote server:

1. A notification will appear indicating that a new device wants to connect.
    
2. Click **Add Device** or **Accept**.
    
3. Verify the device name.
    
4. Click **Save**.
    

The two devices are now paired.

---

# Step 5: Create or Share a Folder

On the device that contains the data:

1. Click **Add Folder**.
    
2. Enter a **Folder Label** (for example, `Documents`).
    
3. Enter a unique **Folder ID** (for example, `documents`).
    
4. Select the folder path to synchronize.
    
5. Under the **Sharing** tab, select the remote device.
    
6. Click **Save**.
    

---

# Step 6: Accept the Shared Folder

On the remote device:

1. A notification appears indicating that a folder has been shared.
    
2. Click **Add**.
    
3. Choose the destination directory where the files should be stored.
    
4. Click **Save**.
    

Syncthing will begin synchronizing the folder automatically.

---

# Step 7: Verify Synchronization

To confirm synchronization:

- The folder status should display **Up to Date**.
    
- Files created or modified on one device should appear on the other device after synchronization.
    
- Check the synchronization progress in the Web GUI.
    

---

# Optional Settings

## Folder Type

When configuring a folder, you can select one of the following types:

- **Send & Receive** – Both devices can read and modify files.
    
- **Send Only** – This device sends changes but does not accept remote modifications.
    
- **Receive Only** – This device receives updates but does not send changes.
    

---

## File Versioning

To protect against accidental deletion or overwriting:

1. Edit the shared folder.
    
2. Open the **File Versioning** tab.
    
3. Choose a versioning method such as:
    
    - Simple Versioning
        
    - Staggered Versioning
        
    - Trash Can Versioning
        
4. Configure the retention settings.
    
5. Save the changes.
    

---

# Troubleshooting

|Issue|Possible Solution|
|---|---|
|Devices not connecting|Verify both Device IDs, ensure both systems have network connectivity, and allow Syncthing through the firewall.|
|Folder not synchronizing|Confirm that the folder is shared with the correct remote device and has been accepted.|
|Files not updating|Verify that both devices show **Connected** and **Up to Date** in the Web GUI.|
|Permission errors|Ensure Syncthing has read/write permissions for the shared directory.|

---

# Best Practices

- Use descriptive device names.
    
- Use unique Folder IDs.
    
- Enable file versioning for important data.
    
- Keep both systems running while the initial synchronization completes.
    
- Regularly monitor the Syncthing Web GUI for synchronization status and errors.
    

---

# Summary

1. Install and start Syncthing on both devices.
    
2. Copy the Device ID from the remote server.
    
3. Add the remote device using **Add Remote Device**.
    
4. Accept the device request on the remote system.
    
5. Create or share a folder.
    
6. Accept the shared folder on the remote device.
    
7. Verify that the synchronization status is **Up to Date**.



# The Syncthing errors have been documented and attached in the Git repository under the **"Issues & Errors"** topic.

## Issues & Errors
https://github.com/vky2161/IT-Info/tree/139a9c7e3b120151c5aeba18c48990a2e86fb4db/Issues%20%26%20Errors