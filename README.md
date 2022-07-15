Given this Github Repo, you have been asked to make sure that the application build process (build/test/release/deploy) can be done each time a developer makes a commit on the main branch using Jenkins declarative pipeline living inside a 'jenkinsfile' inside the repo. Please note that this project as already been setup with Gradle as the build/test tool. At least for the testing part. Infact, currently, if a developer tries to build the project, the resultant 'jar' artifact will produce an error when executed.

no main manifest attribute, in build/libs/caesars-cipher.jar

This error is due to the lack of configuration within the build.gradle file. In order to fix the error above you have to search the documentation to see how you can tell gradle which java class he has to associate with the produced jar file. This is the output of a correctly running app.

Message: in code we trust
Offset: 1
Ciphered message: jo dpef xf usvtu

To help you accomplish this task, here are some of the steps you should go through:

    Install the necessary tools (JVM, gradle, jenkins...)
    Make a new Github repository with the content of the original Repo
    Try to run the build and the tests manually to make sure everything is ok
    Create a Jenkinsfile, and write all the necessary steps, then push it to the remote repo.
    Create a pipeline in jenkins...


Usefull links

    Jenkins Documentation
    Gradle build tool
