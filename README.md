# 📖 Wordpress vs. Kali 🐉

<img width="1494" alt="Screen Shot 2022-10-26 at 12 15 24 PM" src="https://user-images.githubusercontent.com/70921921/198755535-4dac0428-9b6b-4746-94ec-39640e76a66e.png">

## Project: WordPress Penetration Testing

Time Spent: 9 hours 30 minutes. 
> Objective: To find, analyze, recreate and document **five** vulnerabilities effecting WordPress version 4.1.0

### Penetration Testing Report:

### 1. User Enumeration

- [ ] Summary: User Enumeration via logon method. A different message will display based on correct/incorrect entry of a username and password which can lead to a disclosure of account names.
- Vulnerability types: Credential Theft/Discovery
- Tested in version: 4.1.0
- Fixed in version: 4.4 (can install plugin to mitigate)
- [ ] GIF Walkthrough: 

![Kapture 2022-10-28 at 21 35 15](https://user-images.githubusercontent.com/70921921/198755917-5562a951-b888-4e60-ac89-16163c423f2c.gif)
- [ ] Steps to recreate: Go to the login page of the WordPress and test out different usernames. Test common entries such as "admin" or "administrator" and you may get a message saying that the username is not found or that the password for the guessed username is incorrect, thus landing you a potential access point.
- [ ] Affected source code: https://github.com/WordPress/WordPress
- [ ] - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
  
### 2. Stored Cross-Site Scripting via YouTube URL

- [ ] Summary: Using XSS, one can inject malicious JavaScript through a YouTube URL.
- Vulnerability types: Cross-Site Scripting (XSS)
- Tested in version: 4.1.0
- Fixed in version: 4.7.3
- [ ] GIF Walkthrough: 

![Kapture 2022-10-28 at 23 28 45](https://user-images.githubusercontent.com/70921921/198806179-e118036b-5c47-4979-83e0-d7f078360723.gif)
- [ ] Steps to recreate: Create malicious payload through a YouTube URL. Example: ```[embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]```
- [ ] Affected source code: https://github.com/WordPress/WordPress
- [Link 1](http://127.0.0.1:8080/?p=13)

### 3. Cross-Site Scripting via HTML onclick

- [ ] Summary: Creating a post with a simple HTML onclick insertion grants an alert which signifies that we can perform malicious input through the discussion posts on the WordPress blog.
- Vulnerability types: Cross-Site Scripting (XSS)
- Tested in version: 4.1.0
- Fixed in version: 4.2.4
- [ ] GIF Walkthrough: 
![Kapture 2022-10-28 at 23 38 27](https://user-images.githubusercontent.com/70921921/198812363-2cf28bdc-6c9b-478d-a659-db19668ebf79.gif)
- [ ] Steps to recreate: Create a malicious event handler using a method such as HTML with an onclick element to test if you are able to create an alert. An example would be ```<html onclick="alert(1)" style=display:block>test</html>```
- [ ] Affected source code: https://core.trac.wordpress.org/browser/trunk/src/wp-includes/theme.php
- [Link 1](http://127.0.0.1:8080/?p=9)

## Assets

1. [PortSwigger Cross-Site Scripting Cheatsheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with
[Kap](https://getkap.co/) for macOS


## Notes

Many of the problems I faced involved implementation of testing certain vulnerabilities. XSS was the easiest to "set-up" as you can really just spam certain methedologies and such in order to get an alert result, and thus simple scripts could result in some daunting results. 

## License

    Copyright 2022 Nisanth Nadimpalli

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
