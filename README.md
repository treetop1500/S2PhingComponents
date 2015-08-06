# S2PhingComponents
Symfony2 + Phing properties and xml for local, test and production environments.

##Prerequisistes and Assumptions##
1. This set up is customized to a Symfony2 installation utilizing the Symfony3 directory structure.
2. The build scripts are set up to compile sass using compass or gulp-sass. You'll need either installed.
3. The build scripts assume varnish is running on the live environment. Calls to clear varnish cache are made during the live build.
4. The build has a maintenance mode feature that simply changes the 'maintenance' value in the parameters.yml file.  If you wish to take advantage of this, you'll need to add this to your parameters.yml file and set up the detection in your front controller as well as update your routing to display a maintenance page.

##Installation##
1. Download the zip archive and copy the build.xml and build.properties files into your project root (not web root!)
2. Make sure you have phing installed.

##Configuration##
Open the build.properties file and customize the settings to your needs. Replace any instances of '***' with apropriate values, and update the server names and addresses.

##Usage##
To get a list of Phing targets run `sudo phing -l`.  This will list all the main targets as well as subtargets you can call.

###Run the build on one of your environments###
To run the build process on local, test or live, run one of the following, respectively.
`sudo phing build-local`
`sudo phing build-test`
`sudo phing build-live`

###RSYNC###
This set up comes with a target to rsync non-versioned files between environments.
NOTE: You must be SSH'd into one of the environments you with to rsync to/from.  For instance if you are on local, you cannot rsync between test and live.  You would need to SSH to either test or live first.
1. cd to the project root (where your build.xml file is)
2. run `phing rsync`
3. follow the prompts in terminal to complete the process.

