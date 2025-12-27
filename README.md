# ad-lab-2-gpo
In this simple lab, I will take the Windows Server 2019 and client environments I created in the previous lab (https://github.com/johnweghorst/ad-lab) and create some simple GPOs and link them to OUs. First, I will add some desktop icons to our client machine, and then hide them with a GPO in Group Policy Management. I will also set a custom wallpaper for the client. The goal is to demonstrate basic user-based Group Policy management.

# Software and Tools Used
* Oracle VirtualBox
* Windows Server 2019
* Windows 10
* Group Policy Management

# Walkthrough
* First, we need to show some icons on our client desktop. Go to the client machine, right-click the desktop and select Personalize. Then go to Themes, scroll down and click Desktop icon settings. Enable all of them.
<img width="642" height="577" alt="image" src="https://github.com/user-attachments/assets/7829053e-23f1-4059-b738-941f1590cca1" />
<img width="628" height="705" alt="image" src="https://github.com/user-attachments/assets/85edebba-ce3a-4aeb-8774-1bca4129b1db" />

* Now, in Server Manager, go to Tools > Group Policy Management. We’re going to create a GPO to remove these icons from client’s desktop and add a wallpaper.

*	Right-click the _USERS OU that the PowerShell script created in the previous lab, and select Create a GPO in this domain, and Link it here… Name it what you want to.

<img width="798" height="880" alt="image" src="https://github.com/user-attachments/assets/3e0cc61a-8836-46c8-9708-0883971a7826" />

* Then, once it’s created, go to _USERS and find the GPO inside. Right click it and choose Edit.

<img width="975" height="539" alt="image" src="https://github.com/user-attachments/assets/b5152679-4a7e-4d1a-9dbb-3f11a0ccf798" />

* Our policy we want will be under the User Configuration > Policies > Administrative Templates > Desktop folder.

<img width="450" height="722" alt="image" src="https://github.com/user-attachments/assets/bdab0641-52c7-43c9-ac9e-4e6e2fc66515" />

* Here’s all the options we’re looking for.

<img width="975" height="430" alt="image" src="https://github.com/user-attachments/assets/3ad53873-558e-44dc-9820-ddd1df168bce" />

* We’re going to choose to hide all of the individual icons on the desktop. Simply double click each option and tick the radio button for ‘Enabled’.

<img width="428" height="342" alt="image" src="https://github.com/user-attachments/assets/417f945c-c6eb-438c-8be2-5400c0f7d27b" />
<img width="975" height="424" alt="image" src="https://github.com/user-attachments/assets/1bc60ac2-7745-4f87-baaa-2a4529cd929e" />

* We can do some other additional configurations in the Desktop subfolder. We’re going to put a new default wallpaper for our client desktops.

<img width="975" height="286" alt="image" src="https://github.com/user-attachments/assets/a15a49e9-554c-4f44-a486-d9baa3ad9ead" />

* Search the internet on the client PC for an image you would like as a wallpaper. Once you find one, save it to any path you’d like. Make sure it’s a .jpg or a .bmp file. Here’s my wallpaper image and path.

<img width="709" height="327" alt="image" src="https://github.com/user-attachments/assets/556bd998-2f6c-4308-9c70-f7916cf3b1fa" />\

* Now, we’ll click the Desktop Wallpaper configuration in the Desktop subfolder in Group Management Policy Editor. Click Enabled, and put the path to your wallpaper in.

<img width="975" height="904" alt="image" src="https://github.com/user-attachments/assets/3dc2251e-adad-4291-9dc9-9986fb3e3d09" />

* Exit the editor.
* Now on the client PC, this policy won’t take effect until we log out and back in. There’s also the gpudate /force command to update all group policies, but that command isn’t necessary here. Log out of the client machine and log back in. Our group policy was successfully applied! You can log out of the user you're logged in to and log into a different one and the same configurations will be applied as we linked this GPO to the entire _USERS OU.

<img width="975" height="806" alt="image" src="https://github.com/user-attachments/assets/ce85890d-eb0e-40e3-ad18-647bd4997867" />
<img width="975" height="814" alt="image" src="https://github.com/user-attachments/assets/d52c9e20-80f4-4567-af0a-fc9bb0ca97b6" />

* In this lab, I learned how to create and link a basic Group Policy Object (GPO) to an Organizational Unit, apply user-based policy settings, and verify that those policies are automatically enforced at user logon across multiple domain users.
* Thank you for reading this short lab!



