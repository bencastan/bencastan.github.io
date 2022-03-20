title:Ras Pi PoE Hat Fan speed
author: Ben Castan
date: 2022-03-20
status: published

# 16th post for my Blog.
Have been being annoyed by the constant whirrrr of the small fan on 
a Raspberry Pi 4 PoE Hat. The fan just goes all the time.
Did some searching and finally found the solution. Firstly for the version
of Ubuntu I am using the files to be changed are located at 
/boot/firmware/config.txt and not /boot/config.txt as most siolutions say.

So after braving the joy that is StackOverflow I found this link,
<https://stackoverflow.com/questions/68369382/raspberry-pi-poe-fan-hat-with-ubuntu>
It sorted out the location and by applying the fix and a reboot it works.
I am monitoring the RasPi with inxi -s and th etemp does not get above 70DegC so far. It's
not a hot day.
Here are the lines I added.


    dtoverlay=rpi-poe-plus
    dtparam=poe_fan_temp0=70000,poe_fan_temp0_hyst=1000
    dtparam=poe_fan_temp1=75000,poe_fan_temp1_hyst=5000
    dtparam=poe_fan_temp2=80000,poe_fan_temp2_hyst=5000
    dtparam=poe_fan_temp3=82000,poe_fan_temp3_hyst=2000
    
And of course a reboot is needed to apply these settings.