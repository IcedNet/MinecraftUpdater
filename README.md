# MinecraftUpdater
**MinecraftUpdater** is a Python script that automates the tedious process of updating your Minecraft server.

Instead of manually downloading the latest server JAR, uploading it via FTP, stopping the server, backing up your world, and restarting everything — this tool handles it all in one step.

 ## How to Use
1) Navigate to the root of your Minecraft server directory and clone this repository:
   ```bash
   git clone https://github.com/eclair4151/MinecraftUpdater.git
   ```
2) cd into the new MinecraftUpdater folder and run ```python3 update.py``` whenever you want to update the server <br><br>

3) if you want to set up automatted updating, add this script to your cron file. the example below runs every day at 3am<br>
   ```bash
   crontab -e
   0 3 * * * /usr/bin/python3 /full/path/to/update.py
   ```

When run, the script:
- Checks for the latest Minecraft version using Mojang’s manifest API.
- Downloads the new server JAR if an update is available.
- Uses screen to notify players of an impending restart with a 30-second countdown.
- Backs up your world folder into a zip archive.
- Replaces the old server JAR with the new one.
- Restarts the server in a detached screen session.
 
           
## Configuration
Customize the script by editing the config variables:

### Latest vs. Snapshot
UPDATE_TO_SNAPSHOT = \<True,False\> whether to update to the latest snapshot, or main release

### Backup Directory
BACKUP_DIR = \<name of directory to save files\>

### Log File
LOG_FILENAME = \<name of file to save log messages\>

### Ram Settings                
RAM_INITIAL = \<amount of ram to start the server with\><br>
RAM_MAX = \<maximum amount of ram to allocate torwards the server\>           
           
## Scheduling Updates
This script is intended to be run as a cron job.
