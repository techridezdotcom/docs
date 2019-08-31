Convert files from Electronic Software Delivery (ESD) form to Windows Imaging Format* (WIM*) if you need to add updated device drivers.
 

How to convert files:

Windows image files may be in the form of an ESD. Files must be WIM to make updates to drivers. Use the Deployment Image Servicing and Management* (DISM) tool from Microsoft to update image files.

To convert the image files, follow the steps below:

 

Note	Always back up all files before following the process below.
 

Create a folder (ex c:\Win10USB).
Go to the sources directory on your installation media.
Copy the install.esd file to the Win10USB folder.
Open Command Prompt as Administrator (Windows Key + X -> Command Prompt (Admin)).
Change directory to the working directory (cd c:\Win10USB).
Show the available images within the install.esd file.
dism /Get-WimInfo /WimFile:install.esd
<p><img src="https://raw.githubusercontent.com/techridezdotcom/docs/master/23992_image1.png" alt="First image"></p>







Show the available images within the install.esd file

Determine the Index number to modify (in this example we are modifying Index 2)
Export the image to a WIM file.
dism /export-image /SourceImageFile:install.esd /SourceIndex:2 /DestinationImageFile:install.wim /Compress:max /CheckIntegrity

Export the image to a WIM file

You now have an install.wim file alongside the install.esd.

 

Note	If more versions of the OS need to be exported, simply repeat Step 7 changing the corresponding SourceIndex and it will be added.
 

Backup the original install.esd and then replace on your installation media with the new install.wim
