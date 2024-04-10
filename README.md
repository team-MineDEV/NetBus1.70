# NetBus1.70
The late 90s Trojan
NetBus 1.7 removal

Netbus 1.7 was released to the public on 11/14/98. It is basically the same program as version 1.6, but with some new “features” described by Carl here:
What’s new?
Ultra-fast Port scanner.
Port Redirect – redirects data to another host and port.
Server setup – configures the server-exe with some options, like TCP-port and mail notification.
Application Redirect – redirects I/O from console applications to a specified TCP-port.
Possibility to restrict access to only a few IP-numbers.

Removal is essentially the same as 1.60, with the exception that the password (if there is one) is no longer written to the registry. All preferences (including password) are written to an .ini file which will have the same name as the program. Here’s an example patch.ini:

[Settings]
Port1=12345
ServerPwd=Password
LogTraffic=1
MailTo=Me@my.computer
MailFrom=DaBus@localhost
MailHost=your.mail.server

If IP logging is enabled (as it is in the above example), it will write all commands and IP addresses to IP.TXT. Another file (Read on, it’s pretty important) is called “Access.txt”. This file contains the list of IP addresses ALLOWED to connect to the Netbus server.

Therefore, the files to delete are: “Patch.exe”, “Patch.ini”, IP.TXT, as well as removing the startup portion from the registry.

The icon for Patch.exe no longer resembles a torch in windows explorer, now it resembles an Internet Explorer “Channel”. Preliminary results show pretty much the same footprint as 1.6, although now the port could be anything the attacker wants it to be. If you have anything YOU’D like to contribute to this, take a stroll on over to the discussion forum I’ve set up on this site located here.

Network packet captures indicate that the password scheme is padded by one byte (From Ver 1.6) and uses a local file comparison from \%systemroot%\patch.ini. Gibby had the right idea in using a random character generated crack in Netbuster. If you’ve run the Netbuster crack, you’ll notice it could take forever to crack a good password scheme. If you want to protect yourself from this version, create a file using notepad called “Access.txt” with only the IP 127.0.0.0.1 or some other invalid string at the top line, save it to your Windows or WINNT directory (also called “%systemroot%”) make the file attribute “read only”, and reboot. This will keep Netbus 1.7 users from accessing your computer using Netbus 1.7. And if someone tried to slip Netbus 1.7 on your computer, it won’t matter because they can’t connect to you. For the “computer illiterate” or “notepad impaired”, I’ve provided one here. If you are using Explorer, right click, “Save Target As” and save to your Windows or WINNT directory. If you are using Netscape, “Shift-Left-Click” to the same directory. On a personal note, I find it comical that one well placed text file renders this program useless (Even Via Telnet).
