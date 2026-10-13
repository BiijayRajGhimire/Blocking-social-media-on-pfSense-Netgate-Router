# Blocking-social-media-on-pfSense-Netgate-Router
Two reliable methods: DNS blocking with pfBlockerNG (easiest, covers all apps/devices) or manual Firewall Aliases with domain names (no extra package).
Method 1: pfBlockerNG (recommended)  
1.	System > Package Manager > Available Packages → install pfBlockerNG-devel.  
2.	Firewall > pfBlockerNG > run the setup wizard (enables DNSBL + IP reputation).  
3.	Go to DNSBL tab → DNSBL Groups → Add Group. Name it “Social Media.”  
4.	In the group's Domain/Custom List box, paste the domains for the sites you want blocked, e.g.: facebook.com, fbcdn.net, instagram.com, cdninstagram.com, twitter.com, x.com, tiktok.com, tiktokcdn.com, snapchat.com, reddit.com.  
5.	Save, then click Update/Reload under pfBlockerNG > Update to apply the new DNSBL list.  
6.	Ensure client devices use the pfSense box as their DNS server (default on most LANs) no client-side changes needed after that.  
Method 2: Firewall Alias (no package needed)  
1.	Firewall > Aliases > Add. Type: Host(s). Add each social media domain as an entry (pfSense resolves FQDNs periodically).  
2.	Firewall > Rules > LAN > Add a new rule: Action = Block, Source = LAN net, Destination = your new alias.  
3.	Place this rule above any existing “allow all” LAN rule, then Apply Changes
<img width="1088" height="318" alt="image" src="https://github.com/user-attachments/assets/10b04e57-60d2-4a7d-82bc-a9d85d19e22d" />
<img width="1088" height="194" alt="image" src="https://github.com/user-attachments/assets/54ef0770-0a7d-49a3-ac61-87ab5169d317" />
Edit Firewall Rule and choose Lan
<img width="1088" height="356" alt="image" src="https://github.com/user-attachments/assets/c68585de-ea4b-41f0-83b9-0323a249c392" />
<img width="1088" height="207" alt="image" src="https://github.com/user-attachments/assets/a91ddad8-6a54-4209-b2eb-7a7ab44d3052" />
<img width="1088" height="305" alt="image" src="https://github.com/user-attachments/assets/50a4ce4c-598d-4d00-bcf2-56a2bbf62a5c" />
<img width="1088" height="302" alt="image" src="https://github.com/user-attachments/assets/2063ce74-1566-4f71-b949-7284a2ea47c8" />
We can also block social media through DNS Resolver pfsense/Negate Router
<img width="1088" height="416" alt="image" src="https://github.com/user-attachments/assets/4251e2c2-9d70-4740-b5ae-5df7e2a6ed6e" />
<img width="1088" height="331" alt="image" src="https://github.com/user-attachments/assets/5d24f167-b571-487c-82ce-18f02ec092d8" />
<img width="1088" height="329" alt="image" src="https://github.com/user-attachments/assets/82930fb0-73d3-4b5d-886a-1516b524f465" />
<img width="1088" height="148" alt="image" src="https://github.com/user-attachments/assets/c9437e9c-8d77-4164-9e23-8051cc1eb6db" />
After all process Need to conform.
<img width="1088" height="385" alt="image" src="https://github.com/user-attachments/assets/2e68141a-af36-4aad-b08a-495db1944acb" />
Notes  
•	pfBlockerNG (DNS-based) is more reliable since apps use many changing IPs; FQDN aliases can lag behind DNS changes.  
•	Tech-savvy users can bypass DNS blocking with a VPN or alternate DNS — pair with a firewall rule forcing all DNS (port 53/853) through pfSense for stronger enforcement.  
•	Mobile apps often hardcode IPs (bypassing DNS); for full coverage also add the provider's known IP ranges to a blocked alias.  

