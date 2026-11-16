**ASSIGNMENT: 06**

**TRAINED BY: MR. WASEEM ABBAS KHAN**

**SUBMITTED BY: MEHAK ZAHRA**

**COHORT: PSEB-CYBER-ISB-02**

**DEADLINE: 12<sup>TH</sup> NOVEMBER, 2026**

**TASK: A (Recon Workflow)**

Write your own ten-step workflow with your own tool choices. For each
step state the question, the tool, the output and the stopping
condition. Justify one tool choice you made differently from the session

**1.DOMAIN INFORMATION**

**2. DNS INFRASTRUCTURE**

**3. SUBDOMAIN ENUMERATION**

**4. LIVE HOST CONFIRMATION**

**5. PORT SCANNING**

**6. TECHNOLOGY FINGERPRINTING**

**7. DISCOVERY BRUTE FORCE**

**8. URL DISCOVERY**

**9. PARAMETER FUZZING**

**10. MISCONFIGURATION AND TLS**

| **No** | **STEPS** | **QUESTION** | **TOOL** | **OUTPUT** | **STOPPING CONDITION** |
|:--:|----|----|:--:|----|----|
| **1.** | **DOMAIN INFORMATION** | Who owns the domain and when was it created? | whois | Registrar, dates, name servers | Stop when required registration details collected. |
| **2.** | **DNS INFRASTRUCTURE** | What DNS records are configured for the domain? | dig | Mail, hosting and verification records | Required DNS records collected and resolved. |
| **3.** | **SUBDOMAIN ENUMERATION** | What subdomains are associated with the domain? | subfinder, assetfinder, theHarvester | Discovered subdomains and candidate hostnames | Relevant subdomain sources checked and candidate list collected. |
| **4.** | **LIVE HOST CONFIRMATION** | Which discovered hosts are live and responding? | httpx | Live and responsive hosts | All discovered candidates checked and responsive hosts identified. |
| **5.** | **PORT SCANNING** | What services are running on the target host? | nmap | Open ports, running services and their versions | Required ports and services identified and recorded. |
| **6.** | **TECHNOLOGY FINGERPRINTING** | What technologies and versions does the website use? | whatweb, wappalyzer | Website technologies, server details, frameworks and versions | Main technologies and available version information identified. |
| **7.** | **DIRECTORY BRUTE FORCE** | What hidden directories and files exist on the website? | gobuster | Discovered directories, hidden paths and files | Wordlist scan completed and discovered paths recorded. |
| **8.** | **URL DISCOVERY** | What URLs and endpoints are available on the website? | katana | Discovered URLs, endpoints and application routes | Relevant URLs and endpoints collected within the selected crawl depth. |
| **9.** | **PARAMETER FUZZING** | What input points are available on the website? | ffuf | Discovered parameters, input points and hidden paths | Selected parameters and paths tested and results recorded. |
| **10.** | **MISCONFIGURATION AND TLS** | Are there any server misconfigurations or TLS weaknesses? | nikto, sslscan | Server misconfigurations, outdated software and TLS weaknesses | Available web and TLS checks completed and findings documented. |

**JUSTIFICATION OF TOOL – OWASP AMASS**

I selected OWASP Amass alongside Subfinder to compare passive subdomain
discovery with active brute-force enumeration. Subfinder collects
subdomains from public sources, while Amass can use DNS brute-forcing
and recursive discovery to identify additional and potentially hidden
subdomains. This combination provides a broader view of the target's
attack surface.

------------------------------------------------------------------------

**TASK: B (Full Upload Walkthrough)**

Document the DVWA upload module at all four levels with screenshots,
including the Impossible level's source code and what each control
contributes.

1.  Checking that the target is accessible and port discovery

<img src="./media/image1.png" style="width:6.5in;height:2.90278in" />

2.  HTTP headers

<img src="./media/image2.png" style="width:6.5in;height:0.77708in" />

3.  As the target is accessible, now open the DVWA

<img src="./media/image3.png" style="width:6.5in;height:1.71042in" />

4.  Login to DVWA with username: admin and Password: password

<img src="./media/image4.png" style="width:6.5in;height:2.90903in" />

5.  Set the security level to low

<img src="./media/image5.png" style="width:6.5in;height:2.89861in" />

**SECURITY LEVEL:** LOW

- A simple .jpeg image has been upoloaded

<img src="./media/image6.png" style="width:6.5in;height:2.90764in" />

../../hackable/uploads/Untitled.jpeg

- <u>So the path to the image will be</u>:
  http://192.168.100.3/dvwa/hackable/uploads/Untitled.jpeg

<img src="./media/image7.png" style="width:6.5in;height:2.85in" />

- Now create a php shell to check if it uploads or not.

<img src="./media/image8.png" style="width:6.5in;height:0.23403in" />

<img src="./media/image9.png" style="width:6.5in;height:2.90069in" />

- As the security level is low, the simple.php has been uploaded.

<img src="./media/image10.png" style="width:6.5in;height:2.86458in" />

<u>Now from</u>: ../../hackable/uploads/simple.php

- <u>The path will be</u>:
  http://192.168.100.3/dvwa/hackable/uploads/simple.php

- We got the web shell

<img src="./media/image11.png" style="width:6.5in;height:2.74861in" />

- Now running different commands

1.  ls

<img src="./media/image12.png" style="width:6.5in;height:2.72778in" />

2.  pwd

<img src="./media/image13.png" style="width:6.5in;height:2.74861in" />

3.  id

<img src="./media/image14.png" style="width:6.5in;height:2.74861in" />

4.  ip a

<img src="./media/image15.png" style="width:6.5in;height:2.87708in" />

**SECURITY LEVEL:** MEDIUM

<img src="./media/image16.png" style="width:6.5in;height:2.85694in" />

Now make another .php file to upload\
<img src="./media/image17.png" style="width:6.5in;height:0.48125in" />

The file didn’t upload because of security restrictions.

<img src="./media/image18.png" style="width:6.5in;height:2.81597in" />

Now open the suite and open its browser

<img src="./media/image19.png" style="width:6.5in;height:2.99375in" />

Rename the web.php to web.jpeg to bypass the filter

<img src="./media/image20.png" style="width:6.5in;height:0.2375in" />

Choose the newly created file i.e. web.jpeg

<img src="./media/image21.png" style="width:6.5in;height:3.00278in" />

Now turn on the intercept on burpsuite and click “upload”. The request
will be captured before reaching the client side.

<img src="./media/image22.png" style="width:6.5in;height:2.99931in" />

Now send the request to repeater and make changes.

Change the name of web.jpeg to web.php in repeater. Because the filter
was for client side, the file uploaded successfully.

Response: 200 OK

<img src="./media/image23.png" style="width:6.5in;height:2.98889in" />

Now change the name of file from web.jpeg to web.php on the main
requestand forward it.

<img src="./media/image24.png" style="width:6.5in;height:2.96875in" />

Now the image has also been uploaded to browser and we can access the
shell.

<img src="./media/image25.png" style="width:6.5in;height:2.99236in" />

The path will be: http://192.168.100.3/dvwa/hackable/uploads/web.php

We got the web shell

<img src="./media/image26.png" style="width:6.5in;height:2.96875in" />

**SECURITY LEVEL:** HIGH

Now set the security level to high and try uploading image making
changes in the request i.e. rename the file web/jpeg to we.php

<img src="./media/image27.png" style="width:6.5in;height:2.87708in" />

In this case the file was not uploaded because the filter is set for
server side.

<img src="./media/image28.png" style="width:6.5in;height:2.87014in" />

So we will now use double extension trick to bypass the filter.

First we will rename the file web.jpeg to web.jpg.php

The response is 200 OK that means the page is accessible.

<img src="./media/image29.png" style="width:6.5in;height:2.91111in" />

But when we check render it shows that the picture was not uploaded. And
this will be because of filter on server side that it does not accept
the .php file

<img src="./media/image30.png" style="width:6.5in;height:2.88194in" />

Now change the extension of file from web.jpg.php to web.php.jpg and in
this case the file was uploaded.

<img src="./media/image31.png" style="width:6.5in;height:2.90069in" />

Now make the same change in main request and forward it. The file is now
being uploaded.

<img src="./media/image32.png" style="width:6.5in;height:2.90069in" />

The path will be:
<http://192.168.100.3/dvwa/hackable/uploads/web.php.jpg>

And hence we got the shell

<img src="./media/image33.png" style="width:6.5in;height:2.87708in" />

**SECURITY LEVEL:** IMPOSSIBLE

- .jpeg file is uploaded.

<img src="./media/image34.png" style="width:6.5in;height:2.74514in" />

- .php file is not uploaded

<img src="./media/image35.png" style="width:6.5in;height:2.73472in" />

**File Upload Source**

**v**ulnerabilities/upload/source/impossible.php

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;"><p>&lt;?php</p>
<p>if( isset( $_POST[ 'Upload' ] ) ) {</p>
<p>// Check Anti-CSRF token</p>
<p>checkToken( $_REQUEST[ 'user_token' ], $_SESSION[ 'session_token' ],
'index.php' );</p>
<p>// File information</p>
<p>$uploaded_name = $_FILES[ 'uploaded' ][ 'name' ];</p>
<p>$uploaded_ext = substr( $uploaded_name, strrpos( $uploaded_name, '.'
) + 1);</p>
<p>$uploaded_size = $_FILES[ 'uploaded' ][ 'size' ];</p>
<p>$uploaded_type = $_FILES[ 'uploaded' ][ 'type' ];</p>
<p>$uploaded_tmp = $_FILES[ 'uploaded' ][ 'tmp_name' ];</p>
<p>// Where are we going to be writing to?</p>
<p>$target_path = DVWA_WEB_PAGE_TO_ROOT . 'hackable/uploads/';</p>
<p>//$target_file = basename( $uploaded_name, '.' . $uploaded_ext ) .
'-';</p>
<p>$target_file = md5( uniqid() . $uploaded_name ) . '.' .
$uploaded_ext;</p>
<p>$temp_file = ( ( ini_get( 'upload_tmp_dir' ) == '' ) ? (
sys_get_temp_dir() ) : ( ini_get( 'upload_tmp_dir' ) ) );</p>
<p>$temp_file .= DIRECTORY_SEPARATOR . md5( uniqid() . $uploaded_name )
. '.' . $uploaded_ext;</p>
<p>// Is it an image?</p>
<p>if( ( strtolower( $uploaded_ext ) == 'jpg' || strtolower(
$uploaded_ext ) == 'jpeg' || strtolower( $uploaded_ext ) == 'png' )
&amp;&amp;</p>
<p>( $uploaded_size &lt; 100000 ) &amp;&amp;</p>
<p>( $uploaded_type == 'image/jpeg' || $uploaded_type == 'image/png' )
&amp;&amp;</p>
<p>getimagesize( $uploaded_tmp ) ) {</p>
<p>// Strip any metadata, by re-encoding image (Note, using php-Imagick
is recommended over php-GD)</p>
<p>if( $uploaded_type == 'image/jpeg' ) {</p>
<p>$img = imagecreatefromjpeg( $uploaded_tmp );</p>
<p>imagejpeg( $img, $temp_file, 100);</p>
<p>}</p>
<p>else {</p>
<p>$img = imagecreatefrompng( $uploaded_tmp );</p>
<p>imagepng( $img, $temp_file, 9);</p>
<p>}</p>
<p>imagedestroy( $img );</p>
<p>// Can we move the file to the web root from the temp folder?</p>
<p>if( rename( $temp_file, ( getcwd() . DIRECTORY_SEPARATOR .
$target_path . $target_file ) ) ) {</p>
<p>// Yes!</p>
<p>echo "&lt;pre&gt;&lt;a
href='{$target_path}{$target_file}'&gt;{$target_file}&lt;/a&gt;
succesfully uploaded!&lt;/pre&gt;";</p>
<p>}</p>
<p>else {</p>
<p>// No</p>
<p>echo '&lt;pre&gt;Your image was not uploaded.&lt;/pre&gt;';</p>
<p>}</p>
<p>// Delete any temp files</p>
<p>if( file_exists( $temp_file ) )</p>
<p>unlink( $temp_file );</p>
<p>}</p>
<p>else {</p>
<p>// Invalid file</p>
<p>echo '&lt;pre&gt;Your image was not uploaded. We can only accept JPEG
or PNG images.&lt;/pre&gt;';</p>
<p>}</p>
<p>}</p>
<p>// Generate Anti-CSRF token</p>
<p>generateSessionToken();</p>
<p>?&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Explanation of Impossible Level**

As shown in the screenshots, the valid .jpeg image was uploaded
successfully but the renamed PHP web shell was not uploaded. DVWA
displayed the message: "Your image was not uploaded. We can only accept
JPEG or PNG images."

In the previous levels, we were able to bypass some upload checks using
Burp Suite. For example, in Medium level, we changed the Content-Type to
image/jpeg, while in High level, we used a double extension. However,
these methods did not work in the Impossible level because it performs
several checks on the uploaded file.

**Security Controls and Their Purpose**

| **Security Control** | **Code** | **Purpose** |
|----|----|----|
| **CSRF Token** | **checkToken()** | Checks that the upload request comes from a valid session. |
| **Extension Check** | .jpg, .jpeg, .png | Allows only the listed image extensions and rejects PHP files. |
| **File Size Limit** | \$uploaded_size \< 100000 | Allows files smaller than 100,000 bytes. |
| **MIME Type Check** | \$uploaded_type | Checks whether the file is declared as JPEG or PNG. |
| **Image Validation** | getimagesize() | Checks whether the uploaded file is actually a valid image. |
| **Image Re-encoding** | imagecreatefromjpeg/png() and imagejpeg/png() | Creates a new image from the uploaded file, removing unwanted data such as embedded PHP code and metadata. |
| **Random File Name** | md5(uniqid(). \$uploaded_name) | Gives the uploaded image a new random name instead of keeping its original name. |
| **Temporary File Handling** | rename() and unlink() | Processes the image in a temporary location, moves it after successful processing, and removes the temporary file. |

**Conclusion**

The Impossible level provides stronger protection than the Low, Medium
and High levels. It checks the file extension, size, MIME type and
actual image content before accepting an upload. It also re-creates the
image and gives it a random filename.

During testing, the valid JPEG image was accepted, while the PHP web
shell was rejected. This shows that simply changing the file extension
or Content-Type is not enough to bypass these checks. The Impossible
level uses multiple security checks together to prevent malicious file
uploads.

------------------------------------------------------------------------

**TASK: C (Remediation Brief)** Top of Form

One page for a non-technical manager explaining why an unrestricted
upload is critical and what must change, without using the words
'payload' or 'shell'.

Bottom of Form

**Introduction**

File upload is a common feature on websites. Users upload images,
documents and other files for different purposes. However, if a website
does not properly check uploaded files, an attacker may upload harmful
files instead of normal documents or images. This can create a serious
security risk because the uploaded file may be used to access the server
and run unwanted commands. It can put the website, its data and user’s
information at risk.

**Why Is This Vulnerability Critical?**

During testing on DVWA, we found that the Low security level accepted a
PHP file and allowed commands to run on the server. The Medium and High
levels added some checks but these checks could still be bypassed using
different techniques.

If the same weakness exists on a real website, an attacker could:

- Gain access to the web server.

- Access sensitive files and stored information.

- Steal or modify user data.

- Damage website files and affect normal services.

- Use the compromised server for further attacks.

This can result in financial loss, privacy issues and damage to the
company's reputation.

**What Changes Are Required?**

The following security measures should be implemented:

1.  **Check file content:** The server should verify the actual file
    content instead of trusting only its name or type.

2.  **Allow only safe file types:** Only required extensions, such as
    JPG, JPEG and PNG, should be accepted.

3.  **Use random filenames:** Uploaded files should be saved with
    randomly generated names instead of their original names.

4.  **Disable file execution:** The upload folder should be configured
    so that uploaded files cannot run as programs. This is one of the
    most important protections.

5.  **Store files safely:** Files should preferably be stored outside
    the website's main directory. If they need to be accessed through
    the website, they should be provided as downloads.

6.  **Apply size limits and monitoring:** Set file size limits and keep
    records of uploaded files. Suspicious uploads should be checked.

**Conclusion**

Unrestricted file upload is a critical vulnerability because it can give
attackers access to the web server and put important information at
risk. Simply checking the file extension or type is not enough. The
company should apply multiple security controls, especially checking the
actual file content and preventing uploaded files from being executed.
These changes will make the website safer and reduce the risk of
unauthorized access.

------------------------------------------------------------------------
