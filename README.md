# Install Nextcloud Snap in a Raspberry Pi

Have you tried to install nextcloud and couldn't? Or do you want to install it in your home and don't know? This article can help you to make a clean and error-free root installation.

This installation will be for those who want a local server without access from outside the network, use an external disk as the main disk and use https.

First check for updates in your raspberry pi.

> sudo apt update && sudo apt upgrade -y

Now reboot.

> sudo reboot

Now let's install snapd.

> sudo apt install snapd

Reboot.

After rebooting:

> sudo snap install core

And reboot again.

This way you will install snapd completly with no errors.

Now install Nextcloud:

> sudo snap install nextcloud

Enable nextcloud to use external hard drives.

> sudo snap connect nextcloud:removable-media

Now this part is optional. Set Nextcloud to use different ports. If you only gonna use this server for Nextcloud, you don't have to but later if you want to setup, for example, a pi-hole, you will need to execute this command.

> sudo snap set nextcloud ports.http=81 ports.https=444

Now you can enable already https.

> sudo /snap/bin/nextcloud.enable-https self-signed

It will show some errors but that's normal.

Now lets config nextcloud to use a external hdd as a main storage.

Execute the command:

> sudo blkid

This way you will get a list of storages in your device. Identify your external storage. Now we will have to edit a file:

> sudo nano /etc/fstab

Go to end of file and paste this text.


