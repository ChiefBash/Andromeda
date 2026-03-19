<p align="center"><img width="285" height="80" src="https://github.com/user-attachments/assets/875960ea-1f76-4ea7-81b1-cc3379d5dccf" /></p>

# Threadfin

Threadfin (f.k.a. xTeVe) is in simplest terms, a virtual DVR that you can use to play/record/live stream IPTV. Setting up the container is complicated and can take a lot of time. Using these instructions will make the process go as smooth as possible. After doing some research, Threadfin is mostly used as a Docker container but there ware ways to install Threadfin as a separate application itself.

### TUN/COMPOSE.YAML

Ensure the compose.yaml file of the tun stack in Portainer is accurate. This is the section of code if necessary:

```
threadfin:
    image: mgoerentz/threadfin:latest
    container_name: threadfin
    network_mode: service:gluetun
    environment:
      - PUID=1000
      - PGID=1000
      - THREADFIN_PORT=34400
    volumes:
      - ./threadfin/config:/home/threadfin/conf
      - ./threadfin/tmp:/tmp/threadfin:rw
    depends_on:
      gluetun:
    restart: unless-stopped
```

Under the Gluetun service, make sure port 34400 is specified in the port section.

```
service:
  gluetun:
    ports:
      - 34400:34400
```

### PLAYLIST

Click <b>New</b> in the top-left.

<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

Select <b>M3U</b> and click <b>Next</b>.

<img width="1133" height="227" src="https://github.com/user-attachments/assets/772b10ae-cff8-487c-b744-22d11cce2059" />

Add a name, description (optional), add the M3U file and select 2 for the number of tuners/streams. Click <b>Update</b> and <b>Save</b> when complete.

<img width="1127" height="546" src="https://github.com/user-attachments/assets/419c992e-e3aa-4bf6-8656-87043b1e2ebb" />

### XMLTV

Click <b>New</b> in the top-left.

<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

Add a name, description (optional) and the XMLTV link. Click <b>Update</b> and <b>Save</b> when complete.

<img width="1130" height="435" src="https://github.com/user-attachments/assets/d35456fd-61c6-4aec-9595-22468bd86efd" />

### MAPPING

Once the PLAYLIST and XMLTV steps are complete, the channels will begin to populate in the MAPPING section. It takes about 5 minutes for the data to transfer. Once the channels are imported, the channel numbers can be changed/updated. Align the numbers to a cable provider (DISH, AT&T, DirecTV, etc.). It may be best to import the DVR in Plex a few times with different providers first to get an idea of what numbering scheme works best. It also helps to do one channel at a time so it isn't overwhelming.

To activate the channel, follow these steps:

```
Active: ✅

Channel name: Whatever you want

Channel description: BLANK (optional)

Logo URL: https://m3uassets.com/[CHANNEL].

Update Channel Logo: ❌

EPG Category: Select the most relevant one. If one doesn't match, select -.

XMLTV File: The name of the XML file created eariler in the XMLTV section.

XMLTV Channel: Not necessary to add, but something I personally do for peace of mind.
```

Click <b>Done</b> in the bottom-right when complete.

<img width="427" height="62" src="https://github.com/user-attachments/assets/3d6c9e0c-7c31-4503-b7d5-a91c4ef725b6" />

Click <b>Save</b> in the top-left to save all changes.

<img width="255" height="63" src="https://github.com/user-attachments/assets/73f4c0eb-8bde-41ff-9278-ee2039cad1c6" />

### USERS

An administrator account is created when initially setting up Threadfin. Additional users can be added with the following steps:

Click <b>New</b> in the top-left.

<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

Enter a username, strong password and password again to confirm.

```
Web Access: ✅
PMS Access: ❌
M3U Access: ❌
XML Access: ❌
API Access: ❌
```

Click <b>Save</b> in the bottom-right when complete.

<img width="246" height="61" src="https://github.com/user-attachments/assets/c92ba9ac-4b01-4227-b0d9-022a605521f8" />

### SETTINGS
If a setting is not specified here, leave at the default setting.

```
Automatic update of Threadfin: ✅
SSDP: ✅
Number of Tuners: 2 (Equal to the amount concurrent live streams)
EPG Source: XEPG
API Interface: ❌
Schedule for updating (Playlist, XMLTV, Backup): 0000 (Occurs at midnight)
Updates all files at startup: ✅
Location for temporary files: /tmp/threadfin/
Image Caching: ✅
Omit port: ❌
Replace missing program images: ✅
Replace PPV channels title/desc: ✅
Enable Non-ASCII: ❌
Use HTTPS: ❌
Stream Buffer: FFmpeg
Buffer Size: 0.5 MB
Store Buffer in RAM: ✅
User Agent: BLANK (will not work otherwise)
WEB Authentication: ✅
PMS Authentication: ❌
M3U Authentication: ❌
XML Authentication: ❌
API Authentication: ❌
```

Once done, click <b>Save</b> at the top-left.

<img width="377" height="68" src="https://github.com/user-attachments/assets/7e506de6-4f0e-4529-b563-3acb20180b55" />

### DVR INFO
Click <b>Server Information</b> in the top-right.
    
<img width="197" height="56" src="https://github.com/user-attachments/assets/e53b1b0b-b8db-40c0-98f3-4a11869286fc" />

Look for <b>DVR IP</b>.

<img width="233" height="68" src="https://github.com/user-attachments/assets/56d151a1-94c8-42f1-89f3-11983dcbbe1b" />

This IP address (which will be different on each initial setup) is what needs to be imported in Plex to work. Plex will be able to recognize the deivce if you let it search as well (this may take some time).

### IMPORT TO PLEX

Once logged in Plex, go to the server settings.

<img width="244" height="42" src="https://github.com/user-attachments/assets/c0e27719-b575-4c91-ae48-f25ec303ec13" />

In the left sidebar, click <b>Live TV & DVR</b> in the Manage section.
    
<img width="187" height="233" src="https://github.com/user-attachments/assets/5f6d54bc-8227-422f-be83-bb85696a6aee" />

Click <b>Add Another Device</b>.

<img width="283" height="42" src="https://github.com/user-attachments/assets/7adfb6a2-0d80-4376-b290-31bd4d502916" />

Click <b>Don't see your HDHomeRUn device? Enter its network address manually</b>. Enter the DVR IP address from the Threadfin Server Information section and click Connect. If the DVR IP doesn't work, try adding the device IP. [https://device:34400]

<img width="588" height="245" src="https://github.com/user-attachments/assets/5e0b61e9-6047-4c69-a9c9-505acf47606a" />

Pick the best provider and create the DVR. This will take a long time (~ 5-10 minutes) depending on internet speed.
