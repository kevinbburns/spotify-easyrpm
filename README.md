# spotify-easyrpm

![img](https://i.imgur.com/y0tDlYD.png)

Spotify-easyrpm is a script which can download the latest Spotify snapcraft.io package and convert it into an RPM. 
It is also capable of installing, automated updating and storing the Spotify RPMs in a local filesystem repo
for installing Spotify updates alongside regular system updates


 ### Features

 * Set up a build enviornment on your PC and install rpm-build
 * Auto download the latest version of Spotify
 * Convert the snap package to RPM format
 * Install the Spotify RPM
 * Automated Spotify update check
 * Create a local filesystem repo so Spotify can be updated alongside regular updates
 * Fully unattended quiet mode


 ### Howto

```bash
$> spotify-easyrpm
```
  - Regular prompt based mode to create an RPM and optionally install and create an update schedule

```bash
$> spotify-easyrpm --quiet
```

  - Create the RPM
  - Install the Spotify RPM
  - Set up a update timer job
  - Set up a local filesystem repo

```bash
$> spotify-easyrpm --set-channel edge
```

  - Set either "edge" or "stable" version of Spotify client


```bash
$> spotify-easyrpm --create-schedule
```

  - If you previously opted out creating an automated update schedule but now desire it

```bash
$> spotify-easyrpm --remove-schedule
```

  - Removes the schedule and local repo if present

```bash
$> spotify-easyrpm --clean-repo
```

  - Cleans up the local filesystem repo


 ### Requirements

 * Fedora 33/34


 ### Auto Updates

    spotify-easyrpm can create a systemd user timer job which will run daily and 5 minutes after user login. 
    This will call the script to do a light check against the Spotify debian repo for a new release.
    If a new release is found, a build process is kicked off in the background and the final RPM will
    be placed on your machine in a local filesystem repo (/var/cache/spotify-easyrpm).
    The next time you run the system updater or zypper up you will see spotify-client appear as an
    update alongside regular updates.

    If you want to modify the update check timer, the file is at $HOME/.local/share/systemd/user/spotify-easyrpm.timer
    Please see the systemd documentation for more information

    To see a brief summary of the last run do

    systemctl --user status spotify-easyrpm

    If you want to see the full output of the last run you can do

    journalctl --user-unit spotify-easyrpm


 ### Download links (One Click Install)

* [Fedora34](https://github.com/kevinbburns/spotify-easyrpm/raw/master/RPMs/spotify-easyrpm-1.0.0-1.fc34.noarch.rpm)
