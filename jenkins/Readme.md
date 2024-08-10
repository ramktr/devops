#jenkins Home Directory structure:

/var/lib/jenkins
  |_____ jobs --> jobs which got created
  |         |___ job-name
  |                |___ config.xml
  |                |___ builds
  |                |___ nextbuildnumber
  |          
  |_____ config.xml  -> Config file for the jenkins server
  |_____ credentials or secrets  -> All credentials
  |_____ plugins -> Installed plugins
  |_____ nodes --> have nodes information, optional only
  |_____ workspace
            |___ job-name --> where the runtime files are placed( jar\ war)

#jenkins jobs types:

Jobs
|_____ Frestyle  -> Basic script either simple/complex
|_____ Pipeline  -> Job with multiple stages based on the jenkinsfile
|_____ Multibranch -> evolved version of pipeline job, here tasks will get executed based on the branch names
|_____ Multiconfig -> Matrix of jobs, example if JDK 11,17,8 are need to be tested this job can help in testing all the features one by one.
|_____ Folder -> Basically grouping of diff type of jobs. ex: kind of namespaces where grouping of all dev, prod, qa jobs are made seperately.

#Basic Maven Commands:

mvn clean -> Checks for cache and clears the same
mvn compile -> maven build happens with this command
mvn test -> Checking of the test cases
mvn package -> generated war/jar, in the backend all the above cmds are executed