100 days of DevOps: Day 14

There was a problem with Apache server on one of the production servers. I identified the malfunctioning server with curl command from jump server.

Then I logged into the server and checked the status of apache server with "systemctl status httpd" and found it unable to start. I tried restarting, but won't work. 

I then verified the Apache configuration under /etc/httpd/conf/httpd.conf. The port was correctly set to the required port 8088. 

Then I checked with netstat command whether some other process is already using port 8088, and sendmail was using it. As there was no need for that process, I stopped it with systemctl stop sendmail.

I restarted httpd service and Apache server was online, which I verified with curl command again from the jump server.
