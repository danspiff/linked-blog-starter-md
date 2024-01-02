1. Find the wiki called "Cloud Desktop Guide & docker"
2. Goto Cloud Desktop create link in wiki
3. Create new button on Cloud Desktop homepage
4. Give it a name ie dddodg-blink-demo
5. Select x86 architecture
6. Select Virginia for host location
7. Select host type = c6a.4xlarge, memory=32GiB, 500 GiB storagee, 16 Cpus' ($40.00/month)
8. Fleet: (start typing in and filter) - Ring-Site-Desktops
9. Push create my Cloud Desktop button
10. Confirm if querried
11. Watch flow, ~1 hour wait for email
12. cut and post hostname from Cloud Desktop page
	    ssh dev-dsk-dddodg-ld-xxxxxxxxxx.us-east-1.amazon.com
13. create ecdsa keys
	1. no pass phrase
	2. default filenames
	3. ssh-keygen -t ecdsa
14. cat ~/.ssh/id_ecdsa.pug
15. cut and paste above step into Bit bucket account
16. git clone ssh://git@git.rs.ring.com....
17. setup ~/.blinkrc
18. switch to latest branch of clone if needed
19. ./buildme
20. add to ssh config for easier access to cloud desktop