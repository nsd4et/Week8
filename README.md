# Project 8 - Pentesting Live Targets

Time spent: **8+** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration-------------------------
* Insecure Direct Object Reference (IDOR) -----
* SQL Injection (SQLi) ------------------------
* Cross-Site Scripting (XSS) ------------------
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation ------------------

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL: I tried to find an ending in the URLs that had an '=' at the end and I found the URL with that syntax in the staff person directory page. So I just copied and pasted their SQL injection, ' OR SLEEP(5)=0--', in place of the 1 and all of them redirected back to the staff list page except the blue website, which stayed on the employee I had selected. 

Vulnerability #2: Session Hijacking/Fixation: For this one I was a little confused. At first I thought I just posted what they gave me in the URL and it was saying I didn't have permission. I started panciking a little and then I realized I had to add it to the end of one of the website's URL. I tried it on the green and it didn't work. I started panicking again because I thought I just wans't doing it correctly. I then realized it's only suppose to work for one of them. I opened up the blue website in the Firefox and Safari (instead of the green) and I refreshed both sessionIDs. I then logged into the Safari one and then refreshed that sessionID. It didn't change but I thought I would refresh it just incase. I then opened up the sessionID changer in Firefox and copied the sessionID from the Safari one. It was the same as before because of when I tried the green and I was a little nervous it would affect it. Nevertheless, I changed the FirefoxID and refreshed the login page and I was automaically logged in this time. 


## Green

Vulnerability #1: User Enumeration: I took their 'jmonroe99' and first inputed the normal name, jmonroe (without 99) in all three logins and for all of their passwords I used 'test.' All gave me a bolded “log in unsuccessful” except for green website. So at this point I figured it had to be green’s vulnerability. I put jmonroe99 the second time (in all three) and also kept the password the same. This time all three were bolded, including the green. 

Vulnerability #2: XSS: On their description of this vulnerabilitiy, they said “it may be helpful to have one browser window open as a logged-in admin user while another window is attempting a stored XSS attack. It can be the same browser or two different browsers.” So I took the XSS they gave me, <script>alert('Mallory found the XSS!');</script>, and I put it in all the places I could. I logged in as admin and went to add new users, employees, etc. and inserted the XSS in all acceptable fields.None of it worked, in any website. Then I realized I couldn’t access the feedback as an admin and at that point their hint started to make sense. I logged out of admin and copied and pasted their XSS to see if it would work (in the feedback) for all three. After I posted feedback, I realized it would disappear so I couldn't see it except as admin. I logged back in as admin in all three and the only one that had the vulnerability was the green website. I went back and changed mallory to my name for the gif. 


## Red

Vulnerability #1: Insecure Direct Object Reference: In their description they said, "one of the three sites is missing code which would prevent some sensitive information from being made public." I thought back to codepath exercsies from a litlte while ago when we changed the numbering in the URL to access the secret users. I was suppose to find the missing information (the secret user) and the information on the screen ended at 9, so I put 10 for all the three to see what would happen. They all redirected back to the list of staff page except the red showed an employee who was not made public yet.

Vulnerability #2: CSRF: Since the red website was the only website I had left, I knew CRSF had to fall under here. I thought of CSRF tokens so in burp I watched to find a page where I could change different factors. I could change the salespeople. I just sent it to the repeater, changed the name, email and number and sent it back to the website. The http was found so I went back to the salesperson page and it was updated with the information I put. I had to do it under the admin because I couldn't change anything without doing so in burp. 


## Notes

Describe any challenges encountered while doing the work
The first challenge I had was realizing the lab did not connect to the assignment at all. I was very confused unitl Mariah confirmed it in class. I then had to confirm with Professor that WPscan was only for wordpress and not meant for just IP vulnerabilities. I started looking into other scanners and 'Nikto' showed up. This kept giving me same vulneravilities/ similar ones for all the sites. I talked to Professor and he said to try openvas. I found Kali's website article on how to download openvas and set it up but it would not work for me at all. None of the scanners were working and I was losing a lot of time at this point. Since I had the vulnerabilities, I just tested it on all three until I found the outlier for that vulnerability. The lab also did a bad job on explaining how to use Metasploit. I would have spent even more hours trying to figure out how to use it. I think I perfer to do the exploiting myself. 
