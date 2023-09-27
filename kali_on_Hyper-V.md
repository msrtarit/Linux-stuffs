# kali on hyper-V

1. turn on virtualization and Hyper-V from windows optional features.
2. download KALI hyper-v image from 

[https://www.kali.org/get-kali/#kali-virtual-machines](https://www.kali.org/get-kali/#kali-virtual-machines) 

1. decompress the file using 7zip [https://www.7-zip.org/download.html](https://www.7-zip.org/download.html)
    
    cd to the new uncompressed directory
    
    run the “install-vm.bat” file as administrator
    
2. open  hyper-V manager.
    
    from the right side open virtual switch manager
    
    create an “external” virtual switch  and select your PC’s network card from dropdown menu.
    ![Untitled](https://github.com/msrtarit/Linux-stuffs/assets/37762274/4a5f8c37-aa54-4c41-b605-4f9f3cb4c4d9)

    
    
    **now right click on your vm and go to settings.**
    
    ![Untitled 1](https://github.com/msrtarit/Linux-stuffs/assets/37762274/4273ca57-deca-4f7d-ac77-a2980509cd3f)

    
    select the previously created virtual switch
    ![Untitled 2](https://github.com/msrtarit/Linux-stuffs/assets/37762274/61633974-7f19-4dba-be13-f0be1e2cb130)

    
    
    ok we are done with hyper-v settings
    
3. connect to your kali vm
    1. open ethernet setting and assign IP addresses
    2. restart the network interface with 
        1. `sudo ifconfig eth0 down`
        2. `sudo ifconfig eth0 up`
    3. install xrdp using `sudo apt install xrdp xrdp-sesman`
    4. start the xrdp service using 
        1. `sudo systemctl start xrdp`
        2. `sudo systemsctl start xrdp-sesman`
    5. add xrdp to autostart list using
        1. `sudo systemctl enable xrdp`
        2. `sudo systemctl enable xrdp-sesman`
    6. start ssh `sudo service ssh start`
    7. at this momment your kali-vm should be remotely accessible from any RDP client that has access to your assigned IP block.
    8. but in case you still can’t access kali through RDP client,
        1. open terminal ( ctrl+alt+t)
        2. type `kali-tweaks` 
        3. go to virtualization option via keyboard’s arrow key.
        4. press enter and alter the configure state of enhanced mode.
        5. now restart your vm and login from RDP client 🙂
