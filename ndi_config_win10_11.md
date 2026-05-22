
# NDI configuration for streaming multiple OBS channels as one (Windows 10/11)

## Prerequisites

Install [DistroAV and NDI Tools](github.com/DistroAV/DistroAV/wiki/1.-Installation#manual-install-ndi) and [NDI SDK](ndi.video/for-developers/ndi-sdk-download).

Professional information is required for downloading NDI SDK, but no more - after filling required fields, a link to download an installer will be emailed to the given address. Similar information will be similarly required upon launching NDI Tools.

## Discovery Service

### Master system
Discovery Server on the master system allows for channelling of OBS streams from input systems. `ipconfig` in Windows CMD allows for grabbing the master's LAN IPv4 address, where Discovery Server will be running.

Discovery Server's executable is located in `C:\Program Files\NDI\NDI 6 SDK\Bin\Utilities\x64`; or wherever NDI SDK was installed to if the default path has not been used. `NDI Discovery Service.exe` starts the Server; do not close its CMD window.

Open NDI Tools > **Discovery**. Keep Discovery > **Senders** open for monitoring.

### All systems
Open NDI Tools > **Discovery**; **Access Manager**.

In Discovery > **Settings**, connect to the running master Discovery Server.

![](https://i.postimg.cc/DZ7cXT3d/Screenshot-2026-05-21-122814.png)

In Access Manager > **Advanced**, expand **Network Mapping**. Check **Discovery Servers** and fill in **IP Addresses**.

![](https://i.postimg.cc/HkJs4c90/Screenshot-2026-05-21-123328.png)

## DistroAV and NDI Bridge

### Input systems
DistroAV configuration is located in OBS > **Tools**. Make note of **Main Output name** and **Main Output groups**. If either field is edited, selecting OK is necessary to apply the changes.

![](https://i.postimg.cc/kG4FTv4m/Screenshot-2026-05-21-124429.png)

Open NDI Tools > **Bridge** > **Local**. Configure all fields to match with DistroAV configuration, set **Bridge Name** and check **Use Access Manager Groups**.

![](https://i.postimg.cc/ryNm8RJj/Screenshot-2026-05-21-125034.png)

Configure encoding in **Settings and Diagnostics** > **Encoder Settings** also. HEVC is preferred over H.264.

![](https://i.postimg.cc/bwtfwKPb/Screenshot-2026-05-21-125238.png)

## Access Manager

### Master system
In Access Manager > **Groups**, ensure the only group listed under **Receive** is Public. **Memo** can be changed to any description. Select Apply to effect any changes.

![](https://i.postimg.cc/9QF1x9xS/Screenshot-2026-05-21-125605.png)

### Input system

In Access Manager > **Groups**, ensure the only group listed under **Receive** matches that of DistroAV configuration. The only group listed under **Send** should be Public. Select Apply to effect any changes.

![](https://i.postimg.cc/jdNCG313/Screenshot-2026-05-21-130005.png)
![](https://i.postimg.cc/MG4SZqMH/Screenshot-2026-05-21-130241.png)

## Runtime
### Input systems
Have OBS, Discovery and Bridge open. Start the Bridge. **Bandwidth** will show values in Mbits/s once OBS starts capturing data from its sources.

![](https://i.postimg.cc/52hhDpZf/Screenshot-2026-05-21-130914.png)

### Master system
Discovery > Senders will show all visible input systems.

![](https://i.postimg.cc/GhrJgDMV/Screenshot-2026-05-21-131352.png)

Add each input systems as a source to OBS, and configure to select the correct input system for each. OBS streaming from the master can begin once this is done.

![](https://i.postimg.cc/HLCpbpWh/Screenshot-2026-05-21-131559.png)
![](https://i.postimg.cc/90HSnfKC/Screenshot-2026-05-21-131910.png)

