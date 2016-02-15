virl-compute-bootstrap
==============

Prerequisites:

The Network Install requires Internet access. If you are unable to access the Internet, do NOT use this procedure.

The VIRL software stack requires five physical or virtual network interfaces - eth0, eth1, eth2, eth3 and eth4. Configuration need only be applied to eth0, as your primary network access interface. This should be configured with an IP address and default gateway such that you have network access and MUST have Internet access.

If you do not have five physical interfaces, attention must be paid when in STEP 10 below...

install Ubuntu 14.4.3 LTS on your server, creating a default user 'virl'

Login into your VIRL system and enter the following commands

sudo -s

apt-get update

apt-get dist-upgrade -y

apt-get install -y openssh-server git

reboot

On reboot, login as virl. Enter the following commands

git clone https://github.com/VIRL-Open/virl-compute-bootstrap.git

cd virl-compute-bootstrap

sudo -s

./virl-compute-bootstrap.py

You are now presented with a menu. Proceed through the steps sequentially.

NOTE - if you abort the menu sequence and restart, you MUST re-enter the information into the menu fields once more.

Step 1 - Change salt master from controller

- Enter the IP address of the controller InternalNet. If you enter this step, you MUST enter a value. The fields must NOT be blank!

Step 2 - Change salt id from compute1 or salt domain from virl.info

- You may have received instructions to use a specific 'salt id' and 'salt domain', if so, enter the provided values here. If you enter this step, you MUST enter a value. The fields must NOT be blank! Typically the 'salt id' == hostname, 'salt domain' == domain name that you're going to set in the next step.

Step 3 - Change hostname or domain name

- Set the hostname and domain name for your server here, for example, virl-1.mynet.com. If you enter this step, you MUST enter a value. The fields must NOT be blank!

Step 4 - Write out extra.conf

- MUST perform this step even if you have not made any changes in steps 1-3

Step 5 - Change http proxy

- If you are behind a proxy, please set this here

Step 6 - install salt 


After step 6, software will be installed and configured. You must see the following message returned before proceeding to Step 8:

salt-minion start/running, process ####
 *  INFO: Running daemons_running()
 *  INFO: Salt installed!

Step 7 - Test if you are connected to salt-master

- Ensure that you received a return value 'True' before trying to proceed. If you do not, you need to contact your administrator to confirm that you have the correct key and the key has been accepted.

Step 8 - Install virl installer and settings

- Ensure that the step completed and reports no 'Failed' values

Step 9 - Exit

- Software will now be configured

NOTE - if you abort the menu sequence and restart, you MUST re-enter the information into the menu fields (Steps 1 to 5) once more.

Verify that the IP addresses in /etc/network/interfaces match those outlined in /etc/virl.ini

sudo reboot

