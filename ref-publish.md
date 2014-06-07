

### stackoverflow

http://stackoverflow.com/questions/12343452/publish-artifacts-in-travis-ci-how


https://github.com/vorburger/mvnDeployGitHubTravisCI

I've put together an example project at 
https://github.com/vorburger/mvnDeployGitHubTravisCI 
illustrating how to do this (partially based on Hosting a Maven repository on github 
http://stackoverflow.com/questions/14013644/hosting-a-maven-repository-on-github/). 
As explained on the linked answer, the basic idea is to prepare a local repository 
using the maven-deploy-plugin's altDeploymentRepository 
http://maven.apache.org/plugins/maven-deploy-plugin/deploy-mojo.html#altDeploymentRepository, 
and then use the github site-maven-plugin https://github.com/github/maven-plugins 
to push your artifacts to GitHub. Connect Travis to GitHub authentication as explained above.



### travis doc

http://docs.travis-ci.com/user/build-configuration/#Secure-environment-variables

Travis CI supports encryption of environment variables. A configuration with 
secure environment variables might look something like this:

    env:
      global:
        - secure: <encrypted string here>

You can encrypt environment variables using public key attached to your repository. 
The simplest way to do that is to use travis gem:

    gem install travis
    cd my_project
    travis encrypt MY_SECRET_ENV=super_secret



