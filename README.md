[![Coverage Badge](https://rcapi.shippable.com/projects/58931fae59ff230f005a7d34/coverageBadge?branch=master)](https://rc.shippable.com/projects/58931fae59ff230f005a7d34)
[![Run Status](https://rcapi.shippable.com/projects/58931fae59ff230f005a7d34/badge?branch=master)](https://rc.shippable.com/projects/58931fae59ff230f005a7d34)


This is Sample Java project with Jacoco reports
 


###Test Cases that are covered in CI build triggering manually:


1. Matrix build    
     -  when we trigger sample_jacocomatrix project,it will have 3 matrix build 

2. User specified env variable in env tag    
     -  In this project there is one userspecified env( - env=test1 )  mentioned in env tag
   
3. Matrix.include version + user specified env vars     
     - have included one more version openjdk7 along with the env : foo=fubu in matrix. include tag
       env: foo=fubu
4. Matrix.exclude version + user specified env vars 
      - Here we exclude version - jdk: oraclejdk8 with env=test1

5. Matrix.allow_failure version     
   - version oraclejdk7 fails in build ci because of this - if [ "$SHIPPABLE_JDK_VERSION" == "oraclejdk7" ]; then foobar; fi
     so we allow failure for this version 

6. Submodule public    
   - Added public submodule sampleNod which is there in shiptest-rc-ow 
     so whenever sample_jacocomatrix  completes triggering in gitsync we should able to see the submodules sampleNod

7. event trigger project webhook(see payload shows correctly in all cases )    
    - we have set on_start : always,on_success:always where when sample_jacoccomatrix starts  triggering the project webhhook (sampleNod project will  trigger) check payload given in sample_jacoccomatrix is shown in the sampleNod for on_start and on_success build 
 
8. event trigger issue creation(check payload shows correctly)    
    - on_start: always on_success: always , when sample_jacocomatrix builds starts and completes triggering in project(sampleNod) will have issue get created on (on_success and on_start) with the payload given in the sample_jacocomatrix

9. coverage reports    
    - check wheather the coverage report is showing properly 
10. coverage badge
    - check coverage bdge shows properly in github project page properly, when we click on covergae badge it should take us to project dashboard page
    
11. status badge
12. check default pull image (drydock) 
  
 project settings->runs config->low coverage alert (set coverage alert so that we will recive notification when coverage goes below that range 
  
13. Low coverage alert    
     - set low coverage alert below some range with unstable status from project setting->runsConfig, then when coverage report  goes below that range we will receive notification based on the notification we have configured in yml
     we will receive notification in following 

     email:  - shiptest.rc.ow@gmail.com ,
             - shiptest.rc.me@gmail.com
              pwd:Qhode1234
     irc:    - "chat.freenode.net#testrc-irc" , 
             - "chat.freenode.net#testalpha-irc"

     slack:   username: shiptest.rc.ow@gmail.com
              pwd: Qhode1234
              team: shiphitchcockteam 

     hipchat: username: shiptest.rc.ow@gmail.com
              pwd: Qhode1234
              https://shiphitchcock.hipchat.com/chat




 ###Test Cases that are covered when we trigger(rebuild) for 2nd time on the same repo

   
14. cache: true    
15. cache container    
    - cache container it cache a particular folder or file. Here we cache  - $SHIPPABLE_BUILD_DIR/shippable.yml




 ###Test Case that is covered before that we have to do following -> go to project setting and clear cache and then triggering a webhook/manual build

16. clear cache/reset minion    
    - After completing build with cache: true clear cache from project settings-options page and then trigger the project again 
     it should not cache the build which cached before     
     
 ###tag and release build 
     
17. Tag build from ui 
    - create a tag build , when we create a tag  from github ui (even if dont give release name )it will trigger          both tag and release build with tag name given    
18. Release build from github ui
