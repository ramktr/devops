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
|_____ Frestyle  -> General job which can checkout upto from one scm, it can be either simple/complex
|_____ Pipeline  -> Job with multiple stages based on the jenkinsfile
|_____ Multibranch -> evolved version of pipeline job, here tasks will get executed based on the branch names
|_____ Multiconfig -> Matrix of jobs, example if JDK 11,17,8 are need to be tested this job can help in testing all the features one by one.
|_____ Folder -> Basically grouping of diff type of jobs. ex: kind of namespaces where grouping of all dev, prod, qa jobs are made seperately.

#Basic Maven Commands:

mvn clean -> Checks for cache and clears the same
mvn compile -> maven build happens with this command
mvn test -> Checking of the test cases
mvn package -> generated war/jar, in the backend all the above cmds are executed


#Apache tomcat setup
#Java installation -> https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/amazon-linux-install.html
#sudo yum install java-1.8.0-amazon-corretto-devel
#java -version
#wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.93/bin/apache-tomcat-9.0.93.tar.gz
#tar -xvzf apache-tomcat-9.0.93.tar.gz
#cd apache-tomcat-9.0.93/bin/
#./startup.sh
#http://<public IP>:8080/ -> ex: http://54.92.148.46:8080/

#publish over ssh --> Install this plugin before starting. Then look for ssh under 
#dashboard/manage-jenkins/system- ssh and configure the ssh server details, keys, deployment folder location
#Then configure the maven project -> Add maven goals like compile,package in Build Steps. Then define transfer #deails under Post-build Actions
#once deployed check the application 
#http://<public IP>:8080/<application name> -> ex: http://54.92.148.46:8080/addressbook-2.0/

#Pipeline JOb using jenkinsfile
DSL - > Domain specific language
Imperative -> Groovy, with fine granular approach and complex operations.
Declarative -> YAML, which is simple, easy to maintain.

jenkinsfile structure:

pipeline
  |_____ agent -> similar to label
  |_____ stages -> head of all stages
           |___ stage1  ex: build
                  |___ steps -> task to execute on this stage
           |___ stage2  ex: test
                  |___ steps -> task to execute on this stage
           |___ stage3  ex: deploy
                  |___ steps -> task to execute on this stage