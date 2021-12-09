# LVA-Dockers
This is the official place where Nemesysco's LVA7 and QA7 dockers will be hosted and maintained - It is still under construction!

We are working to rebuild the interface and installation and much of what is described below will change and become simpler with future releases.

**Installation**
When you unzip the installer nms_installer-v1.0.5.sh you will find in the installer sub-directory nms_installer/ the installer script nms_installer.sh. 
At this time, you need to run the script as root (the next version will not require it)

The installer script requires to answer a few questions to determine the arguments parameters:

* **Question 1**: Which Linux distribution do you use?

This installer can install the docker for the following distributions:
•	    Ubuntu 16.04, 18.04, 20.04
•	    Debian 10, 11
•	    CentOS 7, 8

If you plan to install on another distribution including Windows and MacOSX, The LVA7 docker platform will work, but you have to install docker manually. (it has not been tested on MacOSX but it should work on MacOSX Intel 64 versions - not on the arm version)

If you are using Linux, you can use the parameter 'docker', which tell the installer to try to install docker. This will work only for one of the supported versions.

Therefore, use the first argument: (Please read to the end)

       _bash nms_installer.sh docker_

* **Question 2**: Which Nemesysco's application do you wish to install?
The docker installer can install Nemesysco's QA7 or LVA7 cores. you need to tell the installer what you want to install:
• For QA7, add the argument: app=QA7
•	For the full LVA7, add the argument: app=LVA7
This will be our second argument (We describe the installation of LVA7): 

       _bash nms_installer.sh docker app=LVA7_

* **Question 3**: Do you have a web server installed on the target machine?
If the answer is NO, and you are using one of the supported distribution, you can instruct the installation to install XAMPP by adding the parameter xampp

To install xampp and then LVA7, execute:

       _sudo bash nms_installer.sh docker app=LVA7 xampp_

Once the installation completes you will be able to access LVA7 at http://127.0.0.1/LVA7/index.php in your web browser

*** If a web server is already installed**
You need to know what url works. The url is used to communicate between part of the site, so http://127.0.0.1 or https://127.0.0.1 usually works. Use:

       _sudo bash nms_installer.sh docker app=LVA7 xampp url=http://127.0.0.1_

Locate the files on the web server which support PHP (on many linux versions it would often, but not always, be at: /var/www/html)
add the argument path=/var/www/html to the installation command.

if your pre-installed web server is xampp, use the argument path=/opt/lampp/htdocs
 
If you think that your path=/var/www/html and url=http://127.0.0.1, you can check it is correct by copying the file nms-single-page-test.php to that path (/var/www/html/nms-simple-page-test.php) and then check the url in your web browser: http://127.0.0.1/nms-simple-page-test.php. You should get the message 'it works'.

If your path and url are correct (I will assume that /var/www/html/nms-simple-page-test.php), you can install the LVA7 instance with:

       _bash nms_installer.sh docker app=LVA7 path=/var/www/html  url=http://127.0.0.1

After the installation you will be able to access LVA7 at http://127.0.0.1/LVA7/index.php in your web browser

**Initialization**

After the installation access the site using your browser:  http://127.0.0.1/LVA7/index.php

***Step 1: Send your SysID to Nemesysco**

Click the "Status" tab and send the results to Nemesysco together with your order form (including the desired level of analysis and number of seats/capacity needed for the site). This information is needed to generate your unique license code.

*** Step 2: Enter your license key**

Once you get your license, Click the tab 'license' and enter the code received from Nemesysco, then click "validate".

Once the License code is processed correctly, you can immediately start processing files.


**Analyze a file (offline analysis)**

Click on analyze, you can choose a file and click analyze.
Use the web API to allow automated analysis of files. The file "QA7-LVA7 for Docker -Site Services.pdf" contains a description of the API.


**Realtime (online) Analysis**

The docker opens the port 12001. Use this port to send streaming packets of 2 seconds of voice data as PCM (8Khz) into the docker to get immediate results.

Study the example codes for the use of offline and online analysis in Python (nmsAnalyze.py)


**Enjoy exploring!
**
