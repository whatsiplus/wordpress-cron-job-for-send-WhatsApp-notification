Configure Cron Job to send WhatsApp message reminders in Wordpress
============================================================

## Contents
- [Windows Server](#windows-server)
- [Linux Distros](#linux-distros)
- [Shared Hosting](#shared-hosting)
    - [CPanel](#cpanel)
    - [Plesk](#plesk)

## Windows Server
1. Login to your Windows Server
2. Press ```Windows Button``` and search for ```Task Scheduler```
3. Under ```Action``` tab, click on ```Create Task```
![image](https://user-images.githubusercontent.com/24620178/143233881-0c2219af-6265-44c3-8741-96e4dc99e26c.png)
4. Fill in the ```Name```, ```Description```, ```Run whether user is logged on or not```, ```Configured for: The Version you're using```
![image](https://user-images.githubusercontent.com/24620178/143234368-96e5ac33-fba2-422a-ab50-d67a9dda4ebd.png)
5. Under ```Trigger``` tab, add a new Trigger and select:
    ```Begin the task: on a schedule```
    ```Repeat task every 15 minutes```
    ```For a duration of indefinitely```
6. Click ```Ok```
![image](https://user-images.githubusercontent.com/24620178/143234934-9476918d-8324-43ad-aade-5df7fca2bf74.png)
7. Open command prompt by hitting ```Windows Button + r```, input ```cmd``` and press enter
![image](https://user-images.githubusercontent.com/24620178/143235982-3b1f1c02-8fcf-43a8-a09c-20281f047aec.png)
9. Run this command ```echo curl https://yourdomain.com/wp-cron.php > %userprofile%\desktop\cron.bat```. Be sure to replace ```yourdomain.com``` with your ```Domain```.
![image](https://user-images.githubusercontent.com/24620178/143235708-97616320-e84e-4430-9d6e-65e6e397bf24.png)
10. Now back to ```Task Scheduler```. Under ```Actions``` tab. Create a new action and browse for the script we created in previous step and press ```OK```
![image](https://user-images.githubusercontent.com/24620178/143236316-7e802ea2-4f01-4695-9efb-5a757e10db3d.png)
11. Under ```Settings``` tab, check the box ```Run task as soon as possible after a scheduled start is missed```
![image](https://user-images.githubusercontent.com/24620178/143237971-ba04afab-e3c4-4485-8eac-ec6e1822810a.png)


## Linux Distros
1. Login to your VPS/VM 
2. execute the command ```crontab -e``` and select the easiest, in our case it's ```1```
![image](https://user-images.githubusercontent.com/24620178/143241107-d19b881d-4d90-44b7-8dd2-2b412eaa86c0.png)
3. Go to the bottom of the file and key in ```*/15 * * * * curl https://yourdomain.com/wp-cron.php > /dev/null 2>&1```. Be sure to replace ```yourdomain.com``` with your ```Domain```
4. Press ```Ctrl + O``` then ```Enter``` then ```Ctrl + X```


## Shared Hosting

### CPanel
1. In CPanel, look for Cron Jobs, your UI might be different, but the process is the same
![image](https://user-images.githubusercontent.com/24620178/143244253-98a34cbe-8a43-42fb-a0bc-3b3c162fc5e0.png)
2. Ensure your settings is the same as the image below. Be sure to replace ```yourdomain.com``` with your Domain in the command ```curl https://yourdomain.com/wp-cron.php```
![image](https://user-images.githubusercontent.com/24620178/143244739-0e9441d5-78f8-4eda-afb3-c730cffdef3b.png)
3. Click on ```Add New Cron job```

### Plesk
1. Select cronjob under ```Tools & Settings -> Tools & Resources -> Scheduled Tasks (Cron Jobs)```
![image](https://user-images.githubusercontent.com/24620178/143246523-a3cf0f3c-6084-4166-b804-0482b638881f.png)
2. Click on ```Add Task```
![image](https://user-images.githubusercontent.com/24620178/143246676-8187f5ce-719e-436a-a48f-45ab886f944e.png)
3. Make sure your settings are as below and replace ```yourdomain.com``` with your Domain
    ```
    Task type: Run a command
    Command  : curl https://yourdomain.com/wp-cron.php
    run      : Cron style */15 * * * *
    ```
![image](https://user-images.githubusercontent.com/24620178/143247229-38b8d604-7fb6-496a-aad3-0cb7b47d5a52.png)
4. Click ```OK```

http://whatsiplus.com/
