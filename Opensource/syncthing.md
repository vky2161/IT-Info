* To  install sycthing in linux machine.
```
sudo apt install syncthing
```
* Then start service.
```
sudo systemctl start syncthing@username.service
```
* The web interface will be available at:
```
http://127.0.0.0:8384
```
* Then you can change the IP from Web UI.

#### For windows
- You can download the Syncthing    [here](https://syncthing.net/downloads/)
- after installation access from web UI.
- And set the username And password for Web Interface.
### Additional commands:

* To  Check its status:
```
systemctl --user status syncthing.service
```

* To  Verify installation
```
syncthing --version
```



#### If Out of sync Error Occurs :
- If you encounter an **"out of sync"** error because files have been deleted (as shown in the picture below) from source machine but it still reflected in replication machine.
- Then  you have to delete those conflicts file and directory using commands  from the affected folder on the Linux machine where Syncthing is installed.


![[Pasted image 20260702115142.png|396]]


![[Pasted image 20260702115552.png]]

