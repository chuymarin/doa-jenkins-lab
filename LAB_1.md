# Lab 1 - Create and Configure a Jenkins Job

**Step 1: Creating the Job**
* Open Jenkins
* Click New Item Link
* Enter Item Name: Hello_World_Job
* Select Freestyle Job
* Click OK button

**Step 2: Configure the Job**
* Fill the description with something like: This is my first Jenkins Job

**Step 3: Add a Build Step**
* Select the "Build" Tab from the top tab menu
* Click on "Add build step" and select "Execute shell" option
* In the command value add the following command:
```
echo "Hello World, my name is (Your Name)"
```
* Click "Save" button
  
**Step 4: Running your Job**
* From the right menu, select "Build Now"
* You will see in the "Build History" the run of your job
* Click on it and then click in "Console Output" from the right menu
* You will see something like:
```
+ echo 'Hello World, my name is (your name)'
Hello World, my name is (your name)
Finished: SUCCESS
```
* Pretty easy right?
* Let's do something else...
\
**Step 5: Configure your Job (again)**
* Click in "Back to Project" link from the right menu
* Click in "Configure" link from the right menu
* Select the option "This project is parameterized"
* Click on "Add Parameter" and select "String Parameter"
* You will need to fill 3 values: Name, Default Value, Description, fill the values as follow:
  * Name: MY_NAME
  * Default Value: (Your Name) #This is actually your name 
  * Description: Choose your name
* Update the command value with the following command:
```
echo "Hello World, my name is ${MY_NAME}"
```
* Click "Save" button
  
**Step 6: Running your Job**
* From the right menu, select "Build with Parameters"
* Now you can choose your name, choose your favorite superhero or any character and click "Build" button
* You will see in the "Build History" a second run of your job
* Click on it and then click in "Console Output" from the right menu
* You will see something like:
```
+ echo 'Hello World, my name is (your chosen name)'
Hello World, my name is (your chosen name)
Finished: SUCCESS
```
* Still easy right?, but now you can choose your name, so everyone can use your job for just saying Hello World
  
**Recap**
Jenkins Jobs can do anything that we want so:
* What do we did?
* What are parameters in a job?
* What is a build step?
* What other things do you think can be done with Jenkins Jobs?
  
**Step 7: Let's do acutally useful stuff**
We are going to configure our job to clone a repository from your github account.
* Go to - [Lab 2 - Create and Configure an SCM Job](https://github.com/chuymarin/doa-jenkins-lab/blob/master/LAB_2.md)

