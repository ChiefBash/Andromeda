<p align="center"><img width="285" height="80" src="https://github.com/user-attachments/assets/875960ea-1f76-4ea7-81b1-cc3379d5dccf" /></p>

<p align="center"><img width="810" height="217" src="https://github.com/user-attachments/assets/6b9c4e2c-4697-40f2-8a4f-1da00f97b941" /></p>

## TORRENT/COMPOSE.YAML

<p align="center">Ensure the compose.yaml file of the torrent stack in Portainer is accurate. This is the section of code if necessary:</p>

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
      - /home/chiefbash/docker/threadfin/config:/home/threadfin/conf
      - /home/chiefbash/docker/threadfin/tmp:/tmp/threadfin:rw
    labels:
      - deunhealth.restart.on.unhealthy=true
    depends_on:
      gluetun:
        condition: service_healthy
        restart: true
    restart: unless-stopped
```

<p align="center">Under the Gluetun service, make sure port 34400 is specified in the port section.</p>

```
service:
  gluetun:
    ports:
      - 34400:34400
```

## PLAYLIST
<p align="center">Click 'New' in the top-left.</p>
<p align="center"><img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" /></p>

<p align="center">Select 'M3U' and click 'Next'.</p>
<p align="center"><img width="1133" height="227" src="https://github.com/user-attachments/assets/772b10ae-cff8-487c-b744-22d11cce2059" /></p>

<p align="center">Add a name, description (optional), add the M3U file and select 2 for the number of tuners/streams. Click 'Update' and 'Save' when complete.</p>
<p align="center"><img width="1127" height="546" src="https://github.com/user-attachments/assets/419c992e-e3aa-4bf6-8656-87043b1e2ebb" /></p>

## XMLTV
<p align="center">Click 'New' in the top-left.</p>
<p align="center"><img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" /></p>

<p>Add a name, description (optional) and the XMLTV link. Click 'Update' and 'Save' when complete.</p>
<p align="center"><img width="1130" height="435" src="https://github.com/user-attachments/assets/d35456fd-61c6-4aec-9595-22468bd86efd" /></p>

## MAPPING
<p align="center">Once the PLAYLIST and XMLTV steps are complete, the channels will begin to populate in the MAPPING section. It takes about 5 minutes for the data to transfer. Once the channels are imported, the channel numbers can be changed/updated. Align the numbers to a cable provider (DISH, AT&T, DirecTV, etc.). It may be best to import the DVR in Plex a few times with different providers first to get an idea of what numbering scheme works best. It also helps to do one channel at a time so it isn't overwhelming.</p>

<p align="center">To activate the channel, follow these steps:</p>
<p align="center"><b>Active</b>: ✅</p>
<p align="center"><b>Channel name</b>: Whatever you want</p>
<p align="center"><b>Channel description</b>: BLANK (optional)</p>
<p align="center"><b>Logo URL</b>: Will populate automatically, no change needs to be made.</p>
<p align="center"><b>Update Channel Logo</b>: ❌</p>
<p align="center"><b>EPG Category</b>: Select the most relevant one. If one doesn't match, select '-'.</p>
<p align="center"><b>XMLTV File</b>: The name of the XML file created eariler in the XMLTV section.</p>
<p align="center"><b>XMLTV Channel</b>: Not necessary to add, but something I personally do for peace of mind.</p>

<p align="center">Click 'Done' in the bottom-right when complete.</p>
<p align="center"><img width="427" height="62" src="https://github.com/user-attachments/assets/3d6c9e0c-7c31-4503-b7d5-a91c4ef725b6" /></p>

<p align="center">Click 'Save' in the top-left to save all changes.</p>
<p align="center"><img width="255" height="63" src="https://github.com/user-attachments/assets/73f4c0eb-8bde-41ff-9278-ee2039cad1c6" /></p>

## USERS
<p align="center">An administrator account is created when initially setting up Threadfin. Additional users can be added with the following steps:</p>
<p align="center">Click 'New' in the top-left.</p>
<p align="center"><img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" /></p>

<p align="center">Enter a username, strong password and password again to confirm.</p>
<p align="center"><b>Web Access</b>: ✅</p>
<p align="center"><b>PMS Access</b>: ❌</p>
<p align="center"><b>M3U Access</b>: ❌</p>
<p align="center"><b>XML Access</b>: ❌</p>
<p align="center"><b>API Access</b>: ❌</p>

<p align="center">Click 'Save' in the bottom-right when complete.</p>
<p align="center"><img width="246" height="61" src="https://github.com/user-attachments/assets/c92ba9ac-4b01-4227-b0d9-022a605521f8" /></p>

## SETTINGS
<p align="center">If a setting is not specified here, leave at the <b>default</b> setting.</p>
<p align="center"><b>Automatic update of Threadfin</b>: ✅</p>
<p align="center"><b>SSDP</b>: ✅</p>
<p align="center"><b>Number of Tuners</b>: 2 (Equal to the amount concurrent live streams. It will be different depending on the provider.)</p>
<p align="center"><b>EPG Source</b>: XEPG</p>
<p align="center"><b>API Interface</b>: ❌</p>
<p align="center"><b>Schedule for updating (Playlist, XMLTV, Backup)</b>: 0000 (Occurs at midnight)</p>
<p align="center"><b>Updates all files at startup</b>: ✅</p>
<p align="center"><b>Location for temporary files</b>: /tmp/threadfin/</p>
<p align="center"><b>Image Caching</b>: ✅</p>
<p align="center"><b>Omit port</b>: ❌</p>
<p align="center"><b>Replace missing program images</b>: ✅</p>
<p align="center"><b>Replace PPV channels title/desc</b>: ✅</p>
<p align="center"><b>Enable Non-ASCII</b>: ❌</p>
<p align="center"><b>Use HTTPS</b>: ❌</p>
<p align="center"><b>Stream Buffer</b>: FFmpeg</p>
<p align="center"><b>Buffer Size</b>: 0.5 MB</p>
<p align="center"><b>Store Buffer in RAM</b>: ✅</p>
<p align="center"><b>User Agent</b>: BLANK (will not work otherwise)</p>
<p align="center"><b>WEB Authentication</b>: ✅</p>
<p align="center"><b>PMS Authentication</b>: ❌</p>
<p align="center"><b>M3U Authentication</b>: ❌</p>
<p align="center"><b>XML Authentication</b>: ❌</p>
<p align="center"><b>API Authentication</b>: ❌</p>
<p align="center">Once done, click Save at the top-left.</p>
<p align="center"><img width="377" height="68" src="https://github.com/user-attachments/assets/7e506de6-4f0e-4529-b563-3acb20180b55" /></p>

## DVR INFO
<p align="center">Click 'Server Information' in the top-right.</p>
<p align="center"><img width="197" height="56" src="https://github.com/user-attachments/assets/e53b1b0b-b8db-40c0-98f3-4a11869286fc" /></p>

<p align="center">Look for 'DVR IP'.</p>
<p align="center"><img width="233" height="68" src="https://github.com/user-attachments/assets/56d151a1-94c8-42f1-89f3-11983dcbbe1b" /></p>
<p align="center">This IP address (which will be different on each initial setup) is what needs to be imported in Plex to work.</p>

## IMPORT TO PLEX
<p align="center">Once logged in Plex, go to the server settings.</p>
<p align="center"><img width="244" height="42" src="https://github.com/user-attachments/assets/c0e27719-b575-4c91-ae48-f25ec303ec13" /></p>

<p align="center">In the left sidebar, click 'Live TV & DVR' in the Manage section.</p>
<p align="center"><img width="187" height="233" src="https://github.com/user-attachments/assets/5f6d54bc-8227-422f-be83-bb85696a6aee" /></p>

<p align="center">Click 'Add Another Device'.</p>
<p align="center"><img width="283" height="42" src="https://github.com/user-attachments/assets/7adfb6a2-0d80-4376-b290-31bd4d502916" /></p>

<p align="center">Threadfin may show up as a device, but 99% of the time, it won't. Click 'Don't see your HDHomeRUn device? Enter its network address manually'. Enter the DVR IP address from the Threadfin Server Information section and click 'Connect'. If the DVR IP doesn't work, try adding the device IP. [https://device:34400]</p>
<p align="center"><img width="588" height="245" src="https://github.com/user-attachments/assets/5e0b61e9-6047-4c69-a9c9-505acf47606a" /></p>

<p align="center">Pick the best provider and create the DVR. This will take a long time (~ 5-10 minutes) depending on internet speed.</p>
