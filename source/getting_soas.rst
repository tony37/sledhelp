===============================
Setting up Sugar using Soas (Sugar on a stick)
===============================

Sugar on a stick is a 'live' implementation of Sugar which can be booted on most PCs without modifying the computers own storage.

Setting up Sugar takes two steps:

1. Making the SOAS usb stick
2. Booting Sugar from the SOAS stick

Downloading the SOAS image
--------------------------------

Link to https: //wiki.sugarlabs.org/go/Sugar_on_a_Stick/Downloads

Click on the x86_64 option. Note this image will only boot on computers with a 64-bit architecture (covers most current computers). 

This is a fairly large file (1GB) and so download may take several minutes.

When complete you should have a file:

	Fedora-SoaS-Live-x86_64-29-1.2.iso

most likely in /home/username/Downloads.


Make a SOAS usb stick
--------------------------------

Start with a 'new' usb stick with as large a capacity as you can afford. In this exaple the stick is 32GB. The stick will be prepared 
using an Ubuntu 18.04 LTS system connected to the internet. 

Insert the stick in a usb port on the computer.

::

 df -h

This shows you the partitions available on your computer. This line is the important one:

::

/dev/sdb1       959M  959M     0 100% /media/tony/label

This means that /dev/sdb1 is the device location of the usb stick and its path is /media/tony/label (where label is the name of your stick, 
often mentioning the manufacturer.  In Linux terms, the device is sdb (where your internal drive is normally sda). 

Copy the image (.iso) to the stick:

::

cd /home/username/Downloads #location of downloaded SOAS image
sudo dcfldd if=Fedora-SoaS-Live-x86_64-29-1.2.iso of=/dev/sdb bs=2M

This last command needs some comments:

dcfldd is a variant of the standard command: dd. It is also available for Windows. 

sudo #requests that this command be executed at superuser. You will get a request for your password (same one you use to login).

Do not put spaces such as if = Fedora, it must be if=Fedora

Make sure of=/dev/sdb points to the location of the usb stick that you discovered with the df - h command. This utility is perfectly 
capable of overwriting your entire hard drive!

bs=2M is somewhat arbitrary, it requests the the copy be made in 2Mb blocks. 


While the copy proceeds, it will report progress as it completes copying a number of blocks. The copy 
is not complete until the prompt line is displayed preceded by a summary of the number of blocks read and written.

Your usb stick is not mounted and so can be removed immediately the copy is complete. It is ready to be used.

Boot SOAS
---------------------------------------

Poweroff the computer.

Insert the stick in a usb port.

Boot the computer.

Use the function keys to enter the setup mode or to select the boot device. Note: UEFI can make this an adventure.

If successful, you will see this or a similar screen. This one is to select a boot device. The exact 
screen depends on the model computer and its firmware.

.. figure:: ../images/getting_soas1.jpg
   :alt: Download Soas
   :width: 500px

Find the device that refers to a usb stick and click on it.

You should get a screen asking for your boot option. Normally, click on enter should start the process. In this casd the default
option is to run tests. Click the esc key (top row far left of keyboard). This should show a lot of text logging the boot process.

.. figure:: ../images/getting_soas2.jpg
   :alt: Booting Soas
   :width: 500px

Soon the first Sugar screen will appear. This is part of a special boot process that occurs only the first time Sugar is started 
after a new install. It asks for a name (the nickname). This name appears along with the XO icon to identify a computer during collaboration. 
Sugar then asks for you to select a color, your gender and your age. In most versions of Sugar it is enough 
just to press the enter key. For Soas, you must click on an age before it will allow you to continue. If all is well, you will 
see the XO icon briefly and then a screen saying your Journal is empty.

This is an unusual property of Sugar version 0.112. Normally, one expects the boot process to end displaying the Home View. To switch 
between views, you need to use the Function keys on the keyboard. 

.. figure:: ../images/getting_soas3.jpg
   :alt: Keyboard
   :width: 500px


The F1 .. F4 keys correspond to the zoom keys on an XO keyboard. The first F1 shows the neighborhood view - essential for using Wifi. 
The second F2 shows the Group or Friends view. This is valuable in collaboration. The third F3 shows the Home View. The fourth F4 shows the Active view - the currently running activity. The F5 key shows the Journal and is where the boot process currently ends. The F6 key is the Frame key - the top rightmost key on the XO keyboard. Click on F3 (it may take more than one press) to see the Home View. This shows a ring of icons, each of which represents an available Sugar activity. 

To end a Sugar session, move the cursor over the XO icon in the center of the Home View and click on the Shutdown option.
 
 




