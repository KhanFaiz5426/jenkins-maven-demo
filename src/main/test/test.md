Procedure
Part A – Environment and tool setup
Step 1: Check Java installation
1. Open Command Prompt.
2. Run:
java -version


3. Verify that Java is installed and its version is displayed.

Your PC already has JDK 21, so you can reuse it.

Step 2: Install Jenkins

For your Windows setup, use the installed Jenkins service rather than downloading another copy of the WAR file.
1. Open Windows Services.
2. Find Jenkins.
3. Start the Jenkins service if it is stopped.
4. Open your browser.
5. Visit:
http://localhost:8080


6. Log in to Jenkins.
7. Complete initial setup if this is a fresh installation.
8. Select Install Suggested Plugins.
9. Create an administrator account if prompted.
Alternative WAR method from the PDF: download jenkins.war and run java -jar jenkins.war. Do not run this alongside your existing Windows Jenkins service on port 8080.

Step 3: Install Apache Maven

1. Download Maven from:
Apache Maven Download2. Extract the downloaded ZIP file.
3. For example, place it inside:
C:\apache-maven-3.10.0


4. Open Windows Search and search for Environment Variables.
5. Select Edit the system environment variables.
6. Click Environment Variables.
7. Under System variables, create:
Variable name: MAVEN_HOME
Variable value: C:\apache-maven-3.10.0


8. Select the existing Path variable and click Edit.
9. Click New and add:
%MAVEN_HOME%\bin


10. Click OK to save.
11. Open a new CMD window and verify:
mvn -v


You should see the Maven version and Java version.

Your PC already has Maven configured inside Jenkins as Maven3. Reuse that installation instead of downloading another copy.
Part B – Configure Jenkins tools
Step 4: Open Global Tool Configuration
1. Open Jenkins Dashboard.
2. Click Manage Jenkins.
3. Open Tools (called Global Tool Configuration in older Jenkins versions).
Step 5: Configure JDK
1. Find the JDK section.
2. Click Add JDK.
3. Enter:
Name: JDK11


4. Uncheck Install automatically.
5. Enter the local JDK installation path.
For your PC:
C:\Program Files\Microsoft\jdk-21.0.12.8-hotspot


6. Save the configuration.

Step 6: Configure Maven
1. Find the Maven section.
2. Click Add Maven.
3. Enter:
Name: Maven3


4. Uncheck Install automatically.
5. Enter Maven installation path:
C:\apache-maven-3.10.0


6. Click Apply and Save.

You already configured Maven3 in your earlier practical, so just verify that it exists. Do not create a duplicate installation.
Part C – Install required Jenkins plugins
Step 7: Open Plugin Manager
1. Go to Manage Jenkins.
2. Select Plugins.
3. Open Available Plugins.
Step 8: Install the required plugins

Search for and install:
Plugin	Purpose
Git Plugin	Connects Jenkins with Git repositories
Maven Integration Plugin	Integrates Maven builds
GitHub Integration Plugin	Supports GitHub integration and webhooks
JUnit Plugin	Displays test reports
Pipeline Plugin	Supports pipeline-based automation

4. Select the required plugins.
5. Click Install.
6. Restart Jenkins if prompted.
Step 9: Verify Jenkins configuration
1. Return to the Jenkins Dashboard.
2. Open Manage Jenkins → Tools.
3. Verify that JDK and Maven are configured.
4. Open Plugins and verify that the required plugins are installed.
Part D – Create a sample Jenkins job
This is a simple verification of the configured environment.

Step 10: Create a Jenkins job
1. Open Jenkins Dashboard.
2. Click New Item.
3. Enter:
MyFirstJenkinsJob


4. Select Freestyle Project.
5. Click OK.
Step 11: Configure a build step
1. Open the Build Steps section.
2. Select Execute Windows batch command.
3. Enter:
echo Jenkins environment is working
java -version
mvn -version


4. Click Apply and Save.

Step 12: Execute the job
1. Open your Jenkins job.
2. Click Build Now.
3. Open Build History.
4. Select the latest build.
5. Click Console Output.
Expected output:
Jenkins environment is working
Java version displayed
Apache Maven version displayed
Finished: SUCCESS


5. Expected Output / Screenshots
Take screenshots of:
1. Java version displayed in CMD.
2. Maven version displayed in CMD.
3. Jenkins Dashboard.
4. Jenkins Tools configuration showing JDK and Maven.
5. Installed Jenkins plugins.
6. Successful Jenkins job Console Output.
6. Conclusion
The Jenkins environment was successfully configured along with Java JDK and Apache Maven. Required plugins were installed to support GitHub integration, automated builds, testing and pipeline execution. This established the foundation for implementing CI/CD workflows.