# Active-Directory

This project will show users a simple approach at creating a virtual server that is running Active Directory. The user will also be able create another user and promote them to domain admin, creation of distribution and security groups. This is a begginer friendly lab that the user can build off of. In future installations I will add a client pc and work with DCHP and DNS.

What is a domain controller? It is a database used by IT to manage users, Distribution/Security Groups, and Devices.

| Users | Get added during the hiring process and disabled or removed during termination. |
| --- | --- |
| Distribution Groups | These are emails the organization subscribes your too such as agency update emails. |
| Security Groups | These are for permissions for resources such as access to certain network drives.  |
| Group Policy | These are rules you create to apply to machines on your network. Such as applying a default printer to all agency devices or adjust password policy. |
| Devices | These are joined by Admin to the domain. It makes those group policies easy to manage. |

What is a domain controller? It is the gatekeeper of specific part of the network. Good for authorization.

Server > AD > DC who checks credentials before access to AD

# Let’s build!

1. We will first need to Download a virtual machine. Any will do!
2. Next to download some disc images also know as .ISO files of our operating system. In this case we are using:
    - Windows Server 2022. You can use an older or newer version (if available) for lab purposes.
    - A Windows 10 or Linux OS to be the client device we will be joining to the domain.

![image alt](https://github.com/Rgonzales92/Active-Directory/blob/0523bc4e96fad0498e2d382ed49f1cf207fe3706/Setup1.png)

Most important parts here are ISO Image where you select the one you downloaded, type is Microsoft unless it is something else such as Linux. Select the version you have. Check skip unattended installation for now and finish.

 3. Next lets right click out machine and go to system:

- Base memory lets do 4096 or keep the default. Now select processor and you can stick with default but I want the machine to process faster so I moved the bar to 2. Hit ok and lets move on.
- Things like Network can stay the same for this lab but we will touch on that in other labs.

 4. Now double the machine you made. First Windows screen you see click next, (IMPORTANT!) on this screen select Standard Desktop experience as the other is command line and we don’t want that. Ok, moving on to the agreement and now you will be asked what install you want. We will choose custom.

1. Next make an easy to use password for lab purposes. Something like Password123!
2. You can hold right ctrl + del to unlock screen

# Active Directory Install

Ok this step is pretty straight forward as soon as your logged in the server manager will appear.

1. Go to Manage > add roles and feats > keep selecting next until server roles and select Active Directory Domain Services, Remote access and click add features make sure group policy management is selected.
    1. Remote access > role services > select DirectAccess and VPN(RAS)/Routing

 2. Keep selecting next until confirmation tab then select install

 3. Once finishied select promote to domain controller

- Add new forest
- Name the domain and add .local if not it will error. example name: lab.local
- forest/domain function select the most up to date server version and set an easy lab friendly password.

 4. After we keep selecting next until you get to the prerequisite check and once done hit install

 5. It will sign you out but now we will see the login looks different. It has our domain title now.

![Example her where my domain was titles AD.local](attachment:b320a344-c5d0-444b-99dd-6aeec9eb4256:Screenshot_2026-05-21_154537.png)

Example her where my domain was titles AD.local

 6. Log in and in our start menu in Windows Admin tools open up Active Directory Users and Computers.

# Create a user

Now to create our first user

1. Ok when AD is open we should you should see the name you gave your domain.local
2. If you click on it then multiple tabs will appear. Lets not use them haha!
3. Its best to make your own. So right click the domain and select new > OU

Whats an OU? It is an Organizational Unit and is one of the building blocks of Active Directory.

It acts as a container or box for organization. Some of the most common are Users, Computers, and Mailbox groups. 

1. With that info lets create an OU titled Users(Add may have one created by default if you can’t delete it then name yours slighlty different).
2. Now that users is made lets right click the Users OU >new > User
3. In this box Fill in the blanks. For logon name I like the format first.lastname

![image.png](attachment:c58af93d-9d8e-450f-9b90-ceaa82c4a94d:image.png)

1. For lab purposes in the password section just use the same easy lab friendly password and uncheck the change password at logon tab.
2. Yay! you created a User. If you double click on them we can add an email such as first.last@domain.local or whatever your domain is called. 
3. Lastly, lets promote this guy to a domain admin. If user account still open and you see member of go to it. If not close out use and right click and select properties. Ok now that we are in member of tab do as such
4. Add > in search box type domain > multiple things should appear >select the one that says Domain Admins > Click check names > ok > apply > ok. 
5. Now log out and login as the user you created. If you made a mistake with password setup just type in username adminstrator and login with those credentials and fix the user you created.
6. Now you have a domain and a domain admin. Next you can build off of this by creating distro groups/security groups and in member of adding them for your user.
