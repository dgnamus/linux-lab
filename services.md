You use systemctl command to start, stop, enable, disable, restart or check the status of the particular service you're insterested in.

Through systemd you can also create your own service or edit what happens. For example, a sample configuration file for a service under /etc/systemd/system/ would look like this:

[Unit]
Description=My Python web application

[Service]
ExecStart=/usr/bin/python3 /opt/code/my_app.py
Restart=always

[Install]
WantedBy=multi-user.target

This is just a simple configuration file with which we made a python web app innto a service that we can now manage in an easier way. 

Additionally, we could also define what needs to happen before the execution of the above program and what should happen post execution, and much more.
