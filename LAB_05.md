# Add Deploy Job to Jenkins Pipeline

**Step 1: Create a nginx directory inside Jenkins_home**
* Go to the jenkins_home: 
```
cd /var/lib/jenkins
```
* Create a nginx directory: 
```
mkdir nginx
```
* Go to the nginx directory that you created: 
```
cd /nginx
```
* **User jenkins must be owner of /var/lib/jenkins/nginx and also the index.html file.**

**Step 2: Create a test index.html file**
* Create a index.html file inside the nginx directory: vi index.html
* Paste the following code to the index.html file and save it.

```
<html>
<header><title>This is title</title></header>
<body>
Hello world
</body>
</html>
```

**Step 3: Turn on a nginx container**
* Run a nginx container mapped to the index.html file as follow:
```
docker run --name nginx -v /var/lib/jenkins/nginx:/usr/share/nginx/html -d  -p 80:80 nginx:1.13.12
```
* Ensure the container is running:
```
docker ps -a
```
* Open nginx to see the index.html that you created.
* Open in your browser: http://YOUR_INSTANCE_IP/
* It must show a simple "Hello World" web page.

**Step 4: Create a Deploy Job**
* Go to Jenkins main page
* Click New Item Link
* Enter Item Name: Deploy_Job
* Select Freestyle Job
* Click OK button

**Step 5: Add Build Environment Step**
* Select the "Build Environment" Tab from the top tab menu
* Select "Delete workspace before build starts"
* Click in "Save" button from the bottom.

**Step 6: Add a Build Step**
* Select the "Build" Tab from the top tab menu
* Click on "Add build step" and select "Copy artifacts from another project" option
* Fill as follow:
  * Project name: Build_Job
  * Which build: Latest successful build
  * Artifacts to copy: dist/hello-world/*
  * Leave the rest fields with the default configuration.
* Click on "Add build step" and select "Execute shell" option
* In the command value add the following command:
```
cp dist/hello-world/* /var/lib/jenkins/nginx
ls -lha
```
* Click "Save" button

**Step 7:  Configure Trigger from Build_job to Deploy_job**
* Configure the Build_Job and go to the Post-build Actions section.
* Clic on "Add post build action"
* Select Archive the artifacts
* Fill Files to archive: **/*
* Clic on "Add post build action"
* Select Trigger parameterized build on other projects
* Fill as follows
  * Projects to build: Deploy_Job
  * Trigger when build is: Stable
* Click "Save" button

**Step 8: Running the NodeJS_Angular_Pipeline**
* In main Jenkins page, click in "NodeJS_Angular_Pipeline" tab
* Click in the "Run" button, to see your pipeline in action
* If all boxes are in green that means you pipeline works correctly
* If the pipeline works, open the nginx page in a browser: http://YOUR_INSTANCE_IP/
* It must show a "Hello World" Angular webpage.

**Recap**
* Check the workspace and output of all jobs and explain what happened
