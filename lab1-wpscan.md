# LAB 1: WPscan

This lab teaches how to setup a WordPress security assessment lab using wpscan on a kali Linux virtual machine and a WordPress server virtual machine. This teaches how to configure the environment and use WPscan.



First, make a new user with the administrator role so that they can install plugins and themes. We are going to set a weak password found from Wikipedia.



Figure 1 - Create New User called Brian with password as Admin

![Figure 1 - Create New User called Brian with password as Admin](assets/lab1-wpscan/figure-001-create-new-user-called-brian-with-password-as-admin.png)






Figure 2 - Administartor Role

![Figure 2 - Administartor Role](assets/lab1-wpscan/figure-002-administartor-role.png)




Install vulnerable plugins and themes which are going to be scanned with WPscan.



Figure 4 - Vulnerable Theme

![Figure 4 - Vulnerable Theme](assets/lab1-wpscan/figure-004-vulnerable-theme.png)




Update WPscan so its database and capabilities are at peak performance



Figure 5 - WPscan Updated

![Figure 5 - WPscan Updated](assets/lab1-wpscan/figure-005-wpscan-updated.png)




Connect the WPscan API key to wpscan so to access the database of vulnerabilities and check if there is any vulnerabilities in the plugins or themes



Figure 6 - API Key

![Figure 6 - API Key](assets/lab1-wpscan/figure-006-api-key.png)




WPScan wordpress url enumerate -p (WPScan checks its database of vulnerabilities for the latest vulnerabilities and identifies plugins that have been installed.



Figure 7 - Output Page 1

![Figure 7 - Output Page 1](assets/lab1-wpscan/figure-007-output-page-1.png)




This image shows the plugin installed and the number of vulnerabilities identified along with fixes.



Figure 8 - Identified Plugin Vulnerabilities

![Figure 8 - Identified Plugin Vulnerabilities](assets/lab1-wpscan/figure-008-identified-plugin-vulnerabilities.png)






Figure 9 - Identified Plugin Vulnerabilities page 2

![Figure 9 - Identified Plugin Vulnerabilities page 2](assets/lab1-wpscan/figure-009-identified-plugin-vulnerabilities-page-2.png)




(The command in figure 10 performs a comprehensive scan that targets plugins using “VP”, themes are targeted with “VT” while “TT” lists the themes and attempts to find associated vulnerabilities. 



Figure 10 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt

![Figure 10 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt](assets/lab1-wpscan/figure-010-wpscan-url-http-192-168-123-65-enumerate-vp-vt-tt.png)




The theme being used has been identified along with 1 vulnerability related to reflected cross site scripting



Figure 11 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt (Identified Theme and associated Vulnerabilities)

![Figure 11 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt (Identified Theme and associated Vulnerabilities)](assets/lab1-wpscan/figure-011-wpscan-url-http-192-168-123-65-enumerate-vp-vt-tt-identified-theme-and-associate.png)




This Image also contains the plugins in use along with 26 vulnerabilities such as reflected cross-site scripting and sensitive data disclosure.



Figure 12 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt (Plugins and Vulnerabilities)

![Figure 12 - wpscan --url http://192.168.123.65 --enumerate vp,vt,tt (Plugins and Vulnerabilities)](assets/lab1-wpscan/figure-012-wpscan-url-http-192-168-123-65-enumerate-vp-vt-tt-plugins-and-vulnerabilities.png)




More plugin Vulnerabilities

Figure 14 - WPscan plugin vulnerability page 3

![Figure 14 - WPscan plugin vulnerability page 3](assets/lab1-wpscan/figure-014-wpscan-plugin-vulnerability-page-3.png)




This page contains the theme WordPress is using and the reflected cross site scripting vulnerability it found.



Figure 15- WPscan theme vulnerabilities

![Figure 15- WPscan theme vulnerabilities](assets/lab1-wpscan/figure-015-wpscan-theme-vulnerabilities.png)




(The command in Figure 16 attempts to brute force login to a account called “Brian” on WordPress using the list of passwords contained in passwords.txt



Figure 16- wpscan --url http://192.168.123.65 --passwords /home/kali/Desktop/passwords.txt --usernames Brian

![Figure 16- wpscan --url http://192.168.123.65 --passwords /home/kali/Desktop/passwords.txt --usernames Brian](assets/lab1-wpscan/figure-016-wpscan-url-http-192-168-123-65-passwords-home-kali-desktop-passwords-txt-usernam.png)




The output shows that a valid combination of credentials was found saying “Username: Brian” and “Password: admin”



Figure 17- Output of "wpscan --url http://192.168.123.65 --passwords /home/kali/Desktop/passwords.txt --usernames Brian"

![Figure 17- Output of "wpscan --url http://192.168.123.65 --passwords /home/kali/Desktop/passwords.txt --usernames Brian"](assets/lab1-wpscan/figure-017-output-of-wpscan-url-http-192-168-123-65-passwords-home-kali-desktop-passwords-t.png)




wpscan --api-token hTaTcGaWxsPHhmEu0DEWtbe5ms9CIZf08MAVz8R7j6A --url http://192.168.123.65 --enumerate ap (Using a API key to find detailed vulnerabilities. The AP option enumerates all plugins and checks each one in the WPscan vulnerability database)





Figure 116 - WPScan API-assisted vulnerability enumeration output

![Figure 116 - WPScan API-assisted vulnerability enumeration output](assets/lab1-wpscan/figure-116-wpscan-api-assisted-vulnerability-enumeration-output.png)


## Security Implications

The 26 plugin vulnerabilities and the Theme vulnerability that were found critically affect the security of the system as information about these vulnerabilities are on WPscan and guides on how to exploit them. These could be used to commit SQL injections to steal user data from the database and 1 of the vulnerabilities include a stored cross site scripting attack which users with administrator access could use to commit these attacks. The best way to solve this is to update the plugins and themes.



## Comparison Table between VP, VT, AP, TT

| VP | VT | AP | TT |
| --- | --- | --- | --- |
| Scans vulnerable Plugins only | Scans Vulnerable Themes only | Scans all plugins regardless of the presence of vulnerabilities | Scans all themes regardless of vulnerabilities |
| Much quicker than scanning all plugins | Much quicker than scanning all themes | Slower than scanning vulnerable plugins only | Slower than scanning vulnerable themes. |



## Week 1 Further Learning: (EXPLOTING VULNERABILITIES)

This section will show one of the exploits found using wpscan be exploited to show the dangers of not implementing solutions provided by WPscan. This section will cover xss attack being executed on the WordPress site. The reason why this vulnerability exists is because the plugin does not sanitise and escape some of its settings, which could allow high privilege users such as admin to perform Stored Cross-Site Scripting attacks even when the unfiltered HTML capability is disallowed (for example in multisite setup).





Figure 18 - Vulnerability Description

![Figure 18 - Vulnerability Description](assets/lab1-week1-further-learning/figure-018-vulnerability-description.png)


### Step 1: Go to the services page of the salon plugin



Figure 19 - Services Section Of the Plugin

![Figure 19 - Services Section Of the Plugin](assets/lab1-week1-further-learning/figure-019-services-section-of-the-plugin.png)




### Step 2: go to the “Title” field



Figure 20 - Title Field

![Figure 20 - Title Field](assets/lab1-week1-further-learning/figure-020-title-field.png)




### Step 3: Change the title from beard trim to &lt;img src=x onerror=alert(1)&gt;



Figure 21- Beard Trim is the Title

![Figure 21- Beard Trim is the Title](assets/lab1-week1-further-learning/figure-021-beard-trim-is-the-title.png)


Title has been changed to &lt;img src=x onerror=alert(1)&gt;



Figure 22 - Title Changed to Code

![Figure 22 - Title Changed to Code](assets/lab1-week1-further-learning/figure-022-title-changed-to-code.png)




### Step 4 go to the assistant’s page and select one of the assistants to edit



Figure 23- Assistant section showing 2 Assistants

![Figure 23- Assistant section showing 2 Assistants](assets/lab1-week1-further-learning/figure-023-assistant-section-showing-2-assistants.png)




Click on limit reservations to the following services



Figure 24 - Limiting Reservations for Mario

![Figure 24 - Limiting Reservations for Mario](assets/lab1-week1-further-learning/figure-024-limiting-reservations-for-mario.png)




### Output of the XSS Attack (The data has entered the web application through an untrusted source through a web request and the data has been included in dynamic content (The box) and is sent to a web user without being checked for harmful content



Figure 25 - Output of the XSS Attack

![Figure 25 - Output of the XSS Attack](assets/lab1-week1-further-learning/figure-025-output-of-the-xss-attack.png)






Figure 26 - Image Icon

![Figure 26 - Image Icon](assets/lab1-week1-further-learning/figure-026-image-icon.png)




## Reflection

This lab has taught me where WordPress vulnerabilities are discovered in the form of plugins and vulnerabilities and how to target them using WPscan such as “vp” for vulnerable plugins and “vt” for vulnerable themes. I have also been reminded of the importance of updating plugins since when I downloaded the latest version of any plugins or themes, there were no vulnerabilities. When using older versions however, many exploits were found and because many websites use WordPress, these vulnerabilities could be exploited to not only harm businesses but customers. The scanning method and what you scan is also important because if you scan all plugins then you trade much more time in return for more results. If you scan vulnerable plugins only, then you reduce that time in exchange for not scanning everything. I have also learnt the importance of using the API key when scanning because it provides access to WPscan’s database of vulnerabilities and will give vulnerabilities of what you are using. 



Strengths and Weaknesses

The strengths of WPscan is that the API Key provides real time vulnerability data instead of relying on outdated local signatures. The output of vulnerabilities provide CVE Refrences and version patches which map directly to actions to patch these explots.  The limitations are that WPscan only works with wordpress. Because it uses a database, it is not good for locating zero-day exploits and the API can only be used 25 times a day. Bruteforcing can take time if the password is strong.
