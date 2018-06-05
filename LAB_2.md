# Lab 2: Create and Configure an SCM Job

**Requirements for this Lab**
* Git >= 2.13.16

**Step 1: Install Git**
* Install git
```
sudo yum install git
```
* Verify git version
```
sudo git version
```

**Step 2: Fork a Repo**
* Go to: https://github.com/chuymarin/doa-angular-hello-world
* Click in the "Fork" button from the top
* This will create the doa-angular-hello-world repository in your account

**Step 3: Create your SSH Keys**
* Open a gitbash terminal
* Execute the following command:
```
ssh-keygen
```
* It will ask yo for some input for path of the key and passphrase, this time leave those as default and just hit enter
* At the end it will show you the Key random art, similar to a qr code but in text.
* Copy the contents of your key, to see the content use the following command:
```
cat /path/to/your/id_rsa.pub
# usually in ~/.ssh/id_rsa.pub
```

**Step 4: Add your ssh key to your github user**
* Go to you github account
* Click the arrow from your profile image and select "Settings"
* Select "SSH and GPG Keys" from the left menu
* Click in "New SSH key" button and fill the values
  * Title: id_rsa
  * Key: (paste the contents of your id_rsa.pub)
* Then click in "Add SSH key" button

**Step 5: Create new credentials in Jenkins**
* Copy the contents of your key, to see the content use the following command:
```
cat /path/to/your/id_rsa
```
* Open a browser and go to Jenkins
* From the left menu click in "Credentials" link
* Then click in "System" link from the right menu
* Click in "Global credentials" link
* Click in "Add Credentials" link from the right menu
* Fill the values as follow:
  * Kind: SSH Username with private key
  * Scope: leave as default
  * Username: your github username
  * Private Key: select "Enter directly" option
  * Key: paste the contents of your id_rsa
  * ID: github-(your github username)
  * Passhphrase: leave empty if you didn't create a passphrase for your key
  * Description: (Your github username) ssh key
* Click in "OK" button

**Step 6: Create an SCM Job**
* Go to Jenkins main page
* Click New Item Link
* Enter Item Name: SCM_Job
* Select Freestyle Job
* Click OK button

**Step 7: Configure the Job**
* Fill the description with something like: GitHub SCM Job

**Step 8: Add an SCM Step**
* Select the "Source Code Management" Tab from the top tab menu
* Select "Git" option
* Fill the Repositories values as follow:
  * Repository URL: paste the ssh url from your doa-angular-hello-world repository
  * You can find that in your repository site, "Clone or Download" button, "Use SSH" link, and copy the URL
  * Credentials: select your created credentials
* Note: Jenkins will try to access your repository, and it will show an error if it is not able to access, selecting your credentials should fix the issue

**Step 9: Add Build Environment Step**
* Select the "Build Environment" Tab from the top tab menu
* Select "Delete workspace before build starts"
* Click in "Save" button from the bottom.

**Step 10: Test your SCM Job**
* From the right menu, select "Build Now"
* You will see in the "Build History" the run of your job
* Click on it and then click in "Console Output" from the right menu
* You will see some git commands executed by jenkins, if success go "Back to Project"
* Click in "Workspace" link, this is he workspace of the job, all files used by the job should be there
* In this case you should see the contents of your repository

**Recap**
* What do we did?
* What is an SCM step?
* What the "Delete workspace before build starts" does? xD
* What other things do you think that can be done after cloning your repository?

**Next:**
* [Lab 3 - Configure Pre-Requisites](https://github.com/chuymarin/doa-jenkins-lab/blob/master/LAB_3.md)
