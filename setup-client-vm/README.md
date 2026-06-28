# Setup - Client VM
- This part details about creating the isolated switch (`vmbr1`) as mentioned in the main `README.md` and the Client VM
## Creating the Isolated Switch (`vmbr1`)
- Note: The reason why I did this was because so I can create a isolated private network separate from my home network and so there would be no interference from my private network to my home network. These VMs are not able to access my home network or the internet unless I add a router or firewall later

- First, I went to the web console and clicked `Create` > `Linux Bridge`

<img width="1185" height="533" alt="image" src="https://github.com/user-attachments/assets/fa427081-2034-452d-a352-6e0a51cc3882" />

- Then, I clicked `Apply configuration` and we can see that the `Active` column is set to `Yes` for `vmbr1`

<img width="1207" height="541" alt="image" src="https://github.com/user-attachments/assets/09cacb18-cf84-4de0-a498-4f2bb4461819" />

- Then, I clicked on `DC01` > `Hardware` and changed the bridge to `vmbr1`

<img width="1307" height="589" alt="image" src="https://github.com/user-attachments/assets/8e778448-cae8-42d4-bb8f-36a7ed3390b5" />

- As we can see, the packets don't even make it out of the VM's NIC. It is completely isolated as that is the setting we applied

<img width="960" height="563" alt="image" src="https://github.com/user-attachments/assets/1fc12007-570f-459b-bef0-1865bce9f283" />

## Setting up the Client VM
- For setting up the Client VM, the steps are very similar, if not, identical to setting up the Domain Controller and so I will skip showing all of the steps

- Update: We are in the process of installing Windows 11 Pro. I chose Windows 11 Pro because Windows 11 Home lacks the business networking features needed for enterprise environments. Most importantly, Home edition cannot join an Active Directory domain

<img width="960" height="599" alt="image" src="https://github.com/user-attachments/assets/076c62ea-fb21-4d09-bbfd-de942f3b59d8" />

- Now, I have arrived at this screen where Microsoft wants me to connect to the internet and login in to a Microsoft account but there is a way to bypass this

<img width="955" height="596" alt="image" src="https://github.com/user-attachments/assets/509100b7-308d-40e2-a4c6-7d286e81a2bd" />

- We press `Fn + Shift + F10` to open up command prompt and type `OOBE\BYPASSNRO` (this reboots the VM into an offline mode, letting us create a traditional local user account). As we can see, after the VM reboots, we get another option at the bottom

<img width="1031" height="646" alt="image" src="https://github.com/user-attachments/assets/a49206ed-3963-469f-a918-017696b63f50" />

- I am waiting...

<img width="949" height="595" alt="image" src="https://github.com/user-attachments/assets/72a91e06-5618-49cb-919b-960db514dd8d" />

- We have finally arrived and the installation was successful

<img width="961" height="596" alt="image" src="https://github.com/user-attachments/assets/f94504a4-cbcb-4ac9-97a3-4c8ec723c3c5" />

- Next thing before I join it to the domain is to set a static IP and point the DNS to the DC. As you can see below, I set the IP address of the Client VM to `192.168.1.201` and the DNS server to `192.168.1.200`

<img width="960" height="600" alt="image" src="https://github.com/user-attachments/assets/d1fd04c7-dafa-4523-b015-2aa32335de81" />

