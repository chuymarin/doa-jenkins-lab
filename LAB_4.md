# Lab 4: Create and Configure a Jenkins Pipeline

**Install Pre-Requisistes**
* git
* node v10.0.0
* npm 3.10.10
* ng 6.0.0

**Step 1: Test Configuration Job**
* Open Jenkins
* Click New Item Link
* Enter Item Name: Test_Configuration
* Select Freestyle Job
* Click OK button

**Step 2: Configure the Job**
* Fill the description with something like: Checking Pre-Requisites

**Step 3: Add a Build Step**
* Select the "Build" Tab from the top tab menu
* Click on "Add build step" and select "Execute shell" option
* In the command value add the following command:
```
git --version
node -v
npm -v
ng -v
```
* Click "Save" button
  
**Step 4: Running your Job**
* From the left menu, select "Build Now"
* You will see in the "Build History" the run of your job
* Click on it and then click in "Console Output" from the left menu
* You will see something like:
```
+ git --version
git version 1.8.3.1
+ node -v
v10.0.0
+ npm -v
3.10.10
+ ng -v
     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/
Angular CLI: 6.0.0
```
* If you are able to see the version of these tools, you can continue with the next step

**Step 1: Create Build_Job**
* Click New Item Link
* Enter Item Name: Build_Job
* Select Freestyle Job
* Click OK button

**Step 3: Configure the Build_Job**
* Fill the description with something like: Checking Pre-Requisites
* Go to the bottom and click "Save" button
* We are going to do more updates later...

**Step 4: Updating SCM_Job Configuration**
* Go to your previously created SCM_Job
* Click in "Configure" link
* Click in "Post-Build Actions" Tab
* Click in "Add post-build action"
* Select "Archive the artifacts" and fill the values as follow:
  * 	Files to archive: `**/*`
* Click in "Add post-build action"
* Select "Trigger parametrized build on other projects" and fill the values as follow:
  * Projects to build: Build_Job
  * Trigger when build is: stable
  * Trigger build without parameters: checked
* Go to the bottom and click "Save" button

**Step 5: Updating Build_Job Configuration**
* Go to your previously created Build_Job
* Click in "Configure" link
* Click in "Build" Tab
* Click in "Add build step"
* Select "Copy artifacts from another project" and fill the values as follow:
  * Project name: SCM_Job
  * Which build: Latest succesful build
  * Stable builds only: checked
  * Leave the rest values empty
* Click in "Add build step"
* Select "Execute shell" and fill the values as follow:
  * Command: 
```
npm install
ng build --prod
```
* Go to the bottom and click "Save" button

**Step 6: Create Pipeline View**
* Click "New View" link from the right menu
* Enter View Name: NodeJS_Angular_Pipeline
* Select: Build Pipeline
* Click OK button

**Step 7: Configure NodeJS_Angular_Pipeline View**
* In "Pipeline Flow" section and "Upstream / downstream config"
  * Select initial job: SCM_Job
* In "Display Options" section"
  * Number of displayed builds: 5
  * Row headers: Just the pipeline number
  * Column headers: Just the build and name number
* Go to bottom and click "OK" button
* Now in the main Jenkins page where you see the list of Jobs you will have 2 tabs
  * All
  * NodeJS_Angular_Pipeline
  
**Step 8: Running the NodeJS_Angular_Pipeline**
* In main Jenkins page, click in "NodeJS_Angular_Pipeline" tab
* Click in the "Run" button, to see your pipeline in action
* If all boxes are in green that means you pipeline works correctly

**Recap**
* Check the workspapce and output of all jobs and explain what happened




