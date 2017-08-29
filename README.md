# POC_Vagrant

## Followed steps for working out problem
Keeping a track of steps I am following to show what I have done so far.
Steps followed so far are below:

### Made Repo
- Created Repo
- Shared Repo Address
- Created Readme and Init local, and initial Commit

### PROBLEM SOLVING
- Looked up basics for working with Vagrant, starting a vagrantfile
- Found Vagrant image that could best fit needs, that is vagrant hosted
- Attempted build (success)
- Tore down build
- Committed
- **PAUSE** For Travel Time Home
- Found problem with vagrant image being used - bad setup
- Continued with dev
- Found article on vagrant basic ubuntu image and investigated
- Found article on configure of basic lamp setup with ubuntu vagrant
- Continued with attempt of inline install via chef script (using service provision)
- Converted commands to basic shell command steps
- **eureka** after run have working server with localhost:8080 , now for some more config
- ran check `dpkg -l | grep "apache2\|mysql-server-5.5\|php5"` to make sure modules installed as reported **confirmed** so far, so good.
- **PAUSE** for food and break
- setup inline file
- played with different configs trying to use alternate method
- realised just needed to query db i didn't need to add Data
- set basic php to query and show all db on mysql daemon
**fin**
***pleaase go to localhost:8080 once built to see resulting index page.***

