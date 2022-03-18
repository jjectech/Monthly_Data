Windows Seup

Part A: Set up the prerequisite tools (Choco, Python & Git)

1.	Open powershell by right-clicking & select “open as administrator”

2.	Copy and Paste the following command & then press “Enter”: 

Set-ExecutionPolicy RemoteSigned 

3.	Copy and Paste the following command & then press “Enter”: 

Set-ExecutionPolicy Bypass -Scope Process -Force; `
  iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

4.	Once chocolatey has been successfully installed, copy and paste the following command, then press “Enter": 

choco install python

5.	Once Python has successfully installed, copy & paste the following command, then press “Enter”: 

choco install git.install

6.	At this point all the tools are installed, now exit the powershell.




Note: If you receive the following error message - Unable to read package from path ‘git.install\git.install.nupkg'.

Then go & delete the “git.install” folder in C:\ProgramData\chocolatey\lib & rerun the command:

choco install git.install  

Or

choco install git -fv  


Part B: Download Emails from michael@jjectech.com

1.	Log on to to JJ EC’s email client: https://qiye.aliyun.com/ using Michael Muli’s username & password.

2.	Once logged in, look for the Air Data folder on the lower left of the screen, & double click on the folder.

3.	You will find thousands of emails, download these emails by forwarding them in groups, to do this you must select multiple files and then press “forward” on the bottom of the screen.  (It is recommended to select all emails which have been received on the same day in order to group a whole month’s emails, also use simple terms like Jan8 as subject of the forwarded emails that were originally received on Jan 9th in Michael’s “Air Data” folder)

4.	Once all forwarded emails for the month have been received in the inbox, open one by one and select “package download”. (a zip file will download for each email, containing 50-60 .eml files)


Part C: Running scripts to process air data

1.	Reopen powershell. (this time normally, not as administrator)

2.	Enter the directory you would like to store files from github, if you want to save them on the Desktop then type the following, & press “Enter”:

cd Desktop

3.	Copy and paste the following and again press “Enter”:

git clone https://github.com/jjectech/Monthly_Data.git

4.	A new folder called “Monthly_Data” is now downloaded, now you need to manually insert all .eml files that were downloaded for each day of the month into the "Emails" folder within the new "Monthly_Data" folder.

5.	Once all .eml files (approx 1000) are directly copied to the “Emails” folder, (without separate sub folders), go back to the old powershell window & copy and paste the following command & then press “Enter”: 

cd Monthly_Data

6.	Lastly copy and paste the final command below in powershell & press “Enter”:

powershell -ExecutionPolicy Bypass -File test3.ps1

7.	You will now find 4 new files located in an “Output” folder (C:\Desktop\Monthly_Data\Emails\Output), named “TVOC.csv”, “PM10.csv”, “PM25.csv” & “HCHO.csv”

