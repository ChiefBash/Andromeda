<img width="285" height="80" src="https://github.com/user-attachments/assets/875960ea-1f76-4ea7-81b1-cc3379d5dccf" />

<img width="810" height="217" src="https://github.com/user-attachments/assets/6b9c4e2c-4697-40f2-8a4f-1da00f97b941" />

## TORRENT/COMPOSE.YAML

<p>Ensure the compose.yaml file of the torrent stack in Portainer is accurate. This is the section of code if necessary:</p>

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

<p>Under the Gluetun service, make sure port 34400 is specified in the port section.</p>

```
service:
  gluetun:
    ports:
      - 34400:34400
```

## PLAYLIST
<p>Click 'New' in the top-left.</p>
<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

<p>Select 'M3U' and click 'Next'.</p>
<img width="1133" height="227" src="https://github.com/user-attachments/assets/772b10ae-cff8-487c-b744-22d11cce2059" />

<p>Add a name, description (optional), add the M3U file and select 2 for the number of tuners/streams. Click 'Update' and 'Save' when complete.</p>
<img width="1127" height="546" src="https://github.com/user-attachments/assets/419c992e-e3aa-4bf6-8656-87043b1e2ebb" />

## XMLTV
<p>Click 'New' in the top-left.</p>
<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

<p>Add a name, description (optional) and the XMLTV link. Click 'Update' and 'Save' when complete.</p>
<img width="1130" height="435" src="https://github.com/user-attachments/assets/d35456fd-61c6-4aec-9595-22468bd86efd" />

## MAPPING
<p>Once the PLAYLIST and XMLTV steps are complete, the channels will begin to populate in the MAPPING section. It takes about 5 minutes for the data to transfer. Once the channels are imported, the channel numbers can be changed/updated. Align the numbers to a cable provider (DISH, AT&T, DirecTV, etc.). It may be best to import the DVR in Plex a few times with different providers first to get an idea of what numbering scheme works best. It also helps to do one channel at a time so it isn't overwhelming.</p>

<p>To activate the channel, follow these steps:</p>
<p><b>Active</b>: ✅</p>
<p><b>Channel name</b>: Whatever you want</p>
<p><b>Channel description</b>: BLANK (optional)</p>
<p><b>Logo URL</b>: Will populate automatically, no change needs to be made.</p>
<p><b>Update Channel Logo</b>: ❌</p>
<p><b>EPG Category</b>: Select the most relevant one. If one doesn't match, select '-'.</p>
<p><b>XMLTV File</b>: The name of the XML file created eariler in the XMLTV section.</p>
<p><b>XMLTV Channel</b>: Not necessary to add, but something I personally do for peace of mind.</p>

<p>Click 'Done' in the bottom-right when complete.</p>
<img width="427" height="62" src="https://github.com/user-attachments/assets/3d6c9e0c-7c31-4503-b7d5-a91c4ef725b6" />

<p>Click 'Save' in the top-left to save all changes.</p>
<img width="255" height="63" src="https://github.com/user-attachments/assets/73f4c0eb-8bde-41ff-9278-ee2039cad1c6" />

## USERS
<p>An administrator account is created when initially setting up Threadfin. Additional users can be added with the following steps:</p>

<p>Click 'New' in the top-left.</p>
<img width="110" height="57" src="https://github.com/user-attachments/assets/5dbcf806-9049-43c4-bff1-5ba8ac6cf3c4" />

<p>Enter a username, strong password and password again to confirm.</p>
<p><b>Web Access</b>: ✅</p>
<p><b>PMS Access</b>: ❌</p>
<p><b>M3U Access</b>: ❌</p>
<p><b>XML Access</b>: ❌</p>
<p><b>API Access</b>: ❌</p>

<p>Click 'Save' in the bottom-right when complete.</p>
<img width="246" height="61" src="https://github.com/user-attachments/assets/c92ba9ac-4b01-4227-b0d9-022a605521f8" />

## SETTINGS
<p><b>Automatic uppdate of Threadin</b>: ✅ (Watchtower will also update the Docker container if necessary)</p>
<p><b>SSDP</b>: ✅</p>
<p><b>Number of Tuners</b>: 2 (Equal to the amount concurrent live streams. It will be different depending on the provider.)</p>
<p><b>EPG Source</b>: XEPG</p>
<p><b>API Interface</b>: ❌</p>
<p><b>Schedule for updating (Playlist, XMLTV, Backup)</b>: 0000 (Occurs at midnight)</p>
<p><b>Updates all files at startup</b>: ✅</p>
<p><b>Location for temporary files</b>: /tmp/threadfin/</p>
<p><b>Image Caching</b>: ✅</p>
<p><b>Omit port</b>: ❌</p>
<p><b>Replace missing program images</b>: ✅</p>
<p><b>Replace PPV channels title/desc</b>: ✅</p>
<p><b>Enable Non-ASCII</b>: ❌</p>
<p><b>Use HTTPS</b>: ❌</p>
<p><b>Stream Buffer</b>: FFmpeg</p>
<p><b>Buffer Size</b>: 0.5 MB</p>
<p><b>Store Buffer in RAM</b>: ✅</p>
<p><b>User Agent</b>: BLANK (will not work otherwise)</p>
<p><b>WEB Authentication</b>: ✅</p>
<p><b>PMS Authentication</b>: ❌</p>
<p><b>M3U Authentication</b>: ❌</p>
<p><b>XML Authentication</b>: ❌</p>
<p><b>API Authentication</b>: ❌</p>
<p>Once done, click Save at the top-left.</p>
<img width="377" height="68" src="https://github.com/user-attachments/assets/7e506de6-4f0e-4529-b563-3acb20180b55" />

## DVR INFO
<p>Click 'Server Information' in the top-right.</p>
<img width="197" height="56" src="https://github.com/user-attachments/assets/e53b1b0b-b8db-40c0-98f3-4a11869286fc" />

<p>Look for 'DVR IP'.</p>
<img width="233" height="68" src="https://github.com/user-attachments/assets/56d151a1-94c8-42f1-89f3-11983dcbbe1b" />
<p>This IP address (which will be different on each intial setup) is what needs to be imported in Plex to work.</p>

## IMPORT TO PLEX
<p>Once logged in Plex, go to the server settings.</p>
<img width="244" height="42" src="https://github.com/user-attachments/assets/c0e27719-b575-4c91-ae48-f25ec303ec13" />

<p>In the left sidebar, click 'Live TV & DVR' in the Manage section.</p>
<img width="187" height="233" src="https://github.com/user-attachments/assets/5f6d54bc-8227-422f-be83-bb85696a6aee" />

<p>Click 'Add Another Device'.</p>
<img width="283" height="42" src="https://github.com/user-attachments/assets/7adfb6a2-0d80-4376-b290-31bd4d502916" />

<p>Threadfin may show up as a device, but 99% of the time, it won't. Click 'Don't see your HDHomeRUn device? Enter its network address manually'. Enter the DVR IP address from the Threadfin Server Information section and click 'Connect'. If the DVR IP doesn't work, try adding the device IP. [https://device:34400]</p>
<img width="588" height="245" src="https://github.com/user-attachments/assets/5e0b61e9-6047-4c69-a9c9-505acf47606a" />

<p>Pick the best provider and create the DVR. This will take a long time (~ 5-10 minutes) depending on internet speed.</p>
