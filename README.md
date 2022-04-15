# Members
Evan Liu
Vicky Chou

# Main Site
https://cse135-cl.site

# Collector Site
https://collector.cse135-cl.site

# Reporting Site
https://reporting.cse135-cl.site

# HW 1

Part 2:

    GitHub Deployment Setup

        To avoid the need to live edit our code, we configured our local and remote machines to allow us to simultaneously push our local code to the remote Apache server as well as the online GitHub cloud. To do this, we first made a bare clone of the repository on GitHub, and then we created a GitHub hook that, when exectued, forcefully overwrites the contents of our local website-related files with their counterparts found on the online repository. Then, we added the location of the cloned bare repository as a Git remote repo on our local devices, as well as the online GitHub repository. Then, after adding edited files to our local Git branch, commiting them and pushing them afterwards, the Git hook on our remote devices runs and syncs the pushed files with our online repository and our server-based ones.

Part 3:

    Step 4: Employ Password Protection

        Grader Website Login Information:

            Username: grader
            Password: cse135grader

        Grader Apache Login Information:

            Username: grader
            Password: grader

            Public SSH Key: (see attached discKey.pub file)
            Private SSH Key: (see attached discKey file)
    
    Step 5: Compress Textual Content

        After configuring gzip to compress our HTML files, we found that these files were significantly smaller bytewise than on our working versions of the files, and also the indentation within the files was changed such that the largest space between two lines was 1 and the largest space between two characters was 1 as well.

    Step 6: Obscure Server Identity

        To obscure our server identity when viewing the response headers sent by our website, our team installed and utilized the ModSecurity application, which is an application that typically moderates request headers sent to an Apache server and checks them against a predefined set of rules, but in our cases can also be used to change the server signature. To do this, we added the following lines to the end of our apache2.conf file located at /etc/apache2/apache2.conf:

            <IfModule mod_security2.c>
                SecServerSignature "CSE135 Server"
            </IfModule>

        Inherently, these lines serve the purpose of changing the default Apache server signature, which displays the version of Apache being run and relevant Port information, to a different specified signature, in our cases "CSE135 Server".