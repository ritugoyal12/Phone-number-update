# Phone-number-update
Script updates phone numbers in embedded in multiple HTML pages using Linux command. The phone numbers are embedded in multiple formats in the pages and are updated to 202-456-1414.The HTML pages are all under an NFS /var/www mount point shared by all servers.
The solution utilizes the following:
1. Sed : to find and replace the phone numbers in /var/www
         eg:  sed -E -i 's/regex/202-456-1414/g' /var/www/*.html
2. regex expressions : to identify the phone numbers in different patterns.
         (+?1?) - optional US country code
         [-. (]?  - optional punctuations
         [0-9]{3} - Area Code eg. 303
         [A-Z0-9]{3} - numeric and letter mnemonics
         
         
---Linux command----
Please refer Command1 in update_phone.txt file to run the command in terminal

The command will change the following formats to 202-456-1414.
##########
###-###-####, ###.###.####, ### ### ###, (###)#######
prefix US country code, letter mnemonics.

The command will not change the following formats:
(###)-###-### : two punctuations marks together. Please refer to command2 in update_phone.txt file. 
         

--Example-- 
 Old Phone number      New number 
 18001234567           202-456-1414
 1-800-123-4567        202-456-1414
 +1 800 123 4567       202-456-1414
 1(800)1234567         202-456-1414
 800-GET-HELP          202-456-1414
(800)GET-HELP          202-456-1414
 
Please refer to the sample input output files in the repo.
