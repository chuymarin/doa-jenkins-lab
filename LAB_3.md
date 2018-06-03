# Create and Configure Jenkins Pipelines

**Requirements for this Lab**
* Node version >= v10.0.0
* NPM version >= 5.0.0
* Angular CLI >= 6.0.0
* Research about how to install these tools in your jenkins server

**Step 1: Install NodeJs**
* Instructions: https://github.com/nodejs/help/wiki/Installation 
* Download bianries https://nodejs.org/download/release/  
* Search version 10.0.0

**Step 2: Install NPM**
* npm comes pre-installed with node, check that version is >= 5.6.0
* If version is below required, upgrade npm version as follow
´´´
npm install -g npm@5.6.6
´´´

**Step 3: Install Angular CLI**
* Angular cli can be installed using npm
´´´
npm install -g angular-cli
´´´
* Verify that angular cli version it is the required:
´´´
ng -v
´´´
* if you need to upgrade the version execute the following command:
´´´
npm install -g @angular/cli@6.0.0
´´´

**Step 4: Set up Symbolic Links**
* Jenins use the binaries from the following path: /usr/sbin/
* In order to Jenkins be able to run these tools we need to set up symbolic links
* First be sure that all version are correct then check where are the binaries
´´´
which node
which npm
which ng
´´´
* For each binary you need to create the symbolic link as follow:
´´´
# ln -s /path/to/binary /usr/sbin/binary
# example
ln -s /usr/local/bin/node /usr/sbin/node
ln -s /usr/local/node/bin/npm /usr/sbin/npm
ln -s /usr/local/bin/ng /usr/sbin/ng
´´´

**Step 5: Verify symbolic links:**
* To verify if symbolic links have been created correctly check each of them as follow:
´´´
ll /usr/sbin | grep node
ll /usr/sbin | grep npm
ll /usr/sbin | grep ng
´´´

**Recap**
* In this lab we learned how to install nad upgrade tools, and set symbolic links for each of them.
