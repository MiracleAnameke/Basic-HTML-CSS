#  Basic HTML & CSS

## Lab Overview

This lab introduces the basics of HTML & CSS and setting up an FTP server on Ubuntu for web content management. Students will create HTML pages, style them using CSS, and learn to manage these files using FTP.

## Preparation

- Internet connectivity & VMware Workstation version 14.0.0 or above required.
- Use Windows 10 VM for HTML/CSS editing and Ubuntu VM for setting up FTP.

## Lab Tasks and Screenshots

### Part 01: Install a Text Editor on Windows 10 VM & Create a Basic Webpage

- **Task**: Install Notepad++ and create a simple HTML page named `mypage.html`.
- **Slide 01**: Screenshot showing Notepad++ with HTML content and the page opened in a browser.
  <img src="https://i.imgur.com/KKX5BqQ.png" height="400px" width="auto" alt="Creating Basic Webpage"/>

### Part 02: Modify Your HTML5 Page

- **Task**: Enhance the basic HTML page by adding more elements and formatting.
- **Slide 02**: Screenshot of the enhanced HTML content in Notepad++ and browser output.
  <img src="https://i.imgur.com/8aQ27CH.png" height="400px" width="auto" alt="Modified HTML Page"/>

### Part 03: Modify Your HTML5 Page Using CSS

- **Task**: Apply CSS to style the HTML page.
- **Slide 03**: Screenshot of HTML and CSS code in Notepad++ and styled content in browser.
  <img src="https://i.imgur.com/W91lRPB.png" height="400px" width="auto" alt="CSS Styled HTML Page"/>

### Part 04: Setup vsFTPd Server on Ubuntu VM

- **Task**: Install and configure vsFTPd on Ubuntu.

  
- **command**  sudo apt-get install vsftpd

  sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.BACK

  sudo nano /etc/vsftpd.conf

- **Configuration changes in /etc/vsftpd.conf:**
  
anonymous_enable=NO

local_enable=YES

write_enable=YES

allow_writeable_chroot=YES

chroot_local_user=YES

file_open_mode=0777

local_umask=022

userlist_enable=YES

userlist_file=/etc/vsftpd.userlist

userlist_deny=NO

- **Slide 04**: A screenshot demonstrating the connection to the FTP server using FileZilla, including the response received from the server.
The output of net config workstation | find "name" using the CMD prompt to verify network configuration..



  <img src="https://i.imgur.com/yZMjtxS.png" height="400px" width="auto" alt="vsFTPd Setup"/>

### Part 05: Test vsFTPd Access Using FileZilla

- **Task**: Connect to the Ubuntu server using FileZilla

**Commands for user creation and directory setup:**

sudo adduser manameke-ftp

sudo mkdir /var/www/html/manameke-ftp

sudo chown nobody:nogroup /var/www/html/manameke-ftp

sudo chmod a-w /var/www/html/manameke-ftp

sudo mkdir /var/www/html/manameke-ftp/files

sudo chown FOLusername-ftp:manameke-ftp /var/www/html/manameke-ftp/files

echo "testing FTP access" | sudo tee /var/www/html/manameke-ftp/files/ftp_test.txt

echo "manameke-ftp" | sudo tee -a /etc/vsftpd.userlist

sudo systemctl restart vsftpd

- **Slide 05**: A screenshot showing the successful login of the user to the FTP server and the empty directory listing after the initial connection before directory corrections.
Include the command prompt output to display the network configuration.


  <img src="https://i.imgur.com/oo6f1xQ.png" width="auto" alt="Testing vsFTPd Access"/>

### Part 06: Final Configurations and Testing FTP Access

- **Task**: Finalize FTP setup and verify the user can access, view, the `ftp_test.txt` file.
- **Slide 06**: Screenshot showing the directory listing in FileZilla and ability to access the file.
  <img src="https://i.imgur.com/6XzVyD5.png" height="400px" width="auto" alt="Final FTP Configurations"/>
