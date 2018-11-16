
# Title: Queuing up email from the command line

## Easier access to email and great for time management 


### List of commands used:
- cd
- sudo 
- chmod
- echo
- |
- ">"
- hostname 
- bash

### Setup Instructions:

1. Must install SSMTP package, which delivers email from a local computer to a configured mailhost (e.g. Gmail, Yahoo, etc.)

      ##### Important note: SSMTP contains sendmail package, which you will actually use for email delivery

2. Most Linux distributions have sendmail, to check if your computer has it run *sendmail*

3. If you do, success! If you don't run the following command: sudo apt install ssmtp

4. Next, locate the config file /etc/ssmtp/ssmtp.conf by going into your root and following the next lines:
	sudo su
	chmod +x /etc/ssmtp/ssmtp.conf
	chmod +r /etc/ssmtp/ssmtp.conf

5. Then nano into the file and configure as following:
		root=postmaster
		mailhub=smtp.gmail.com:587
		rewriteDomain=gmail.com
		hostname=<your hostname> ## run the command hostname to find out what your hostname is
		UseTLS=YES
		UseSTARTTLS=YES
		AuthUser=<email username>
		AuthPass= app password, which you'll have to configure on gmail
		AuthMethod=LOGIN

6. Once you configure the file, save, and *exit* from the root. 

7. In your preferred directory, create a file where you will include your email message. Call it mail.txt or something similar. Edit the file and include a message.

8. Second to last step, create in the same directory where you stored your mail.txt, your script file and call it sendEmail.sh. 

   In the sendEmail.sh file, include the following script:
	
		#!/bin/bash

		echo "Subject: hello" | sendmail -v email address(here) < mail.txt

9. Save and run the script! *bash sendEmail.sh*
   
