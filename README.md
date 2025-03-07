# HoneySnare
 A modular honeypot that captures IP addresses, usernames, passwords, and commands from various protocols, currently supporting SSH and HTTP. Key functionalities include SSH and HTTP honeypot emulation, credential logging, command auditing, and a dashboard for visualizing attack data

# Loggers
HoneySnare has three loggers configured. Loggers will route to either cmd_audits.log, creds_audits.log (for SSH), and http_audit.log (for HTTP) log files for information capture.

`cmd_audits.log`: Captures IP address, username, password, and all commands supplied.

`creds_audits.log`: Captures IP address, username, and password, comma seperated. Used to see how many hosts attempt to connect to SSH_HONEYPY.

`http_audit.log`: Captures IP address, username, password.

The log files will be located in `../ssh_honeypy/log_files/..`

# Types of Honeypots

This honeypot was written with modularity in mind to support future honeypot types (Telnet, HTTPS, SMTP, etc). As of right now there are two honeypot types supported.

**SSH**
The project started out with only supported SSH. Use the following instructions above to provision an SSH-based honeypot which emulates a basic shell.

💡 `-t / --tarpit`: A tarpit is a security mechanism designed to slow down or delay the attempts of an attacker trying to brute-force login credentials. Leveraging Python's time module, a very long SSH-banner is sent to a connecting shell session. The only way to get out of the session is by closing the terminal.

**HTTP**
Using Python Flask as a basic template to provision a simple web service, HoneySnare impersonates a default WordPress wp-admin login page. Username / password pairs are collected.

There are default credentials accepted, admin and password. Username and password can be changed using the `-u / --username: Username`. `-w / --password`: Password arguments.

The web-based honeypot runs on `port 5000` by default. This can be changed using the `-p / --port` flag option.

💡 There is currently not a dashboard panel supported for HTTP-based results. This is a future scope.
