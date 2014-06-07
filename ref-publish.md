

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


### travis doc 

New Deployment Providers
Joshua Anderson, 17 May 2014


#### GitHub Releases

When you create a git tag, Travis CI can automatically upload your files 
to the resulting GitHub Release. Here is a minimal .travis.yml to get you started.

    deploy:
      provider: releases
      api-key: <GitHub Oauth Token>
      file: <File to Upload>
      skip_cleanup: true
      on:
        tags: true
        all_branches: true

We especially recommend using the travis tool to set up GitHub Releases, as it will 
automatially setup a oauth key with the correct scopes and encrypts it for you.

    $ travis setup releases

Read more: http://docs.travis-ci.com/user/deployment/releases/


