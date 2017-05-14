# raspberry-scripts
Include some very basic but very useful script!  (i.e Auto send the IP of pi, Some of configure file ...) 


Configure
====
If you want to get the IP (cause DHCP random IP for raspberry, so we need to know it when the Pi restart everytime!
To do that, you can use the script call `send_ip.py`, put it at your home work directory. for me:
    
    /home/pi/scripts/send_ip.py

and then let rc.local know you have new mission to run after boot the Pi

    vim /etc/rc.local

and then make something change as below show.
    
    # Print the IP address
	_IP=$(hostname -I) || true
	if [ "$_IP" ]; then
  	  printf "My IP address is %s\n" "$_IP"
      python /home/pi/scripts/send_ip.py	# New line your add ~
	fi
	exit 0

If you can't received email, you should configure the boot-optional
Assume you have HDMI connected, and you can put the below command to open a configure windows!
    
    sudo raspi-config

And then select Boot Optional -> and login after network working (something like that word ~)

