!SLIDE

# Deployment & Operations <br/>at PlayUp #

<br/>
### Ash McKenzie ###
#### March 27th 2012 ####


!SLIDE bullets
  
# About me #

* Sys Admin nine or so years
* Have worked with Solaris, RedHat EL, Gentoo
* Developer five or so years
* Have worked with Perl, PHP and now Ruby


!SLIDE bullets

<img src="playup-logo.png" alt="PlayUp logo" />

* Offices in eight countries
* We're obsessed with sport, ALL sport!
* We build applications and games around live sport
* Majority of development in Melbourne office
* Just released v2 of our iOS app


!SLIDE bullets

# Sports Data Team #

* Team I work in :)
* Five of us, all in Melbourne
* Develop Sports Data API
* Process FTP uploaded sport XML <br/>from five data providers<br/>for nine sports<br/>with 54 leagues
* Produce consistent RESTful JSON API


!SLIDE bullets

# Our clients #

<img src="playup-ios-logo.jpg" alt="PlayUp iOS logo" />

* PlayUp iOS app
* PlayUp Android app (coming soon)
* A number of internal R&D apps


!SLIDE

# Setup #


!SLIDE bullets smbullets

# Then #

<img src="horse-and-cart.jpg" alt="Horse and cart" />

* AWS based
* Lots of manual testing before deployment
* Production deployment once or twice a week
* Deployment was basic shell scripts
* Environments out of sync
* Devs had limited responsibility after commit


!SLIDE bullets incremental

# Now #

* <img src="astro-boy.jpg" alt="Astro boy" />


!SLIDE bullets smbullets

.notes Github flow master branch always deployable, pull requests great for code review, build lights are great - highly visible

# Development #

* AWS based
* Follow the 'Github flow' process
* Take full advantage of Github's pull request system
* Use git commit tags for clarity e.g. [api, db_schema]
* Jenkins CI performs all our tests
* Automated UAT deployment upon green light
* Use of build lights, CCMenu offline CI notifications


!SLIDE bullets smbullets

# Deployment #

* Shared role
* Deployment three to eight times a week
* Deployment is a push button affair
* Commit to production under 30 mins
* Sweet SSH script that uses AWS autoscale tags for host id
* Deployment email sent with git commit log
* Deployments tagged and service description JSON dropped
* <img src="service-description.jpg" alt="Service description" />


!SLIDE bullets incremental

# Future setup #

* <img src="back-to-the-future.jpg" alt="Back to the Future" />


!SLIDE bullets smbullets

# Future / very soon #

* Switch to Ubuntu 10.04
* Take full advantage of AWS auto scaling
* Full Puppet / Chef server provisioning
* Real-time sport events using PUB/SUB


!SLIDE bullets smbullets

.notes RDS not used to cross region replication can occur

# Technology #

* Ruby 1.9, PHP 5.3
* nginx, Passenger, Varnish
* MySQL 5.0 (not RDS), Redis 2.2
* New Relic RPM, Munin, Nagios
* RVM (I prefer rbenv)
* Capistrano


!SLIDE bullets

# OpsDev #

* Valuable being fully aware of environment
* Sharing deployment makes you think carefully about commits
* Ongoing invislble line of responsility.. good & bad ?
* Personally feel more comfortable knowing entire setup
* 


!SLIDE bullets

# Challenges #

* Incoming sport XML accuracy
* JSON API data validation
* Centralising API cache
* PHP and Ruby in one codebase (effectively two apps)
* Reduce Jenkins CI processing time


!SLIDE bullets

# Thank-you! #

* Github flow<br/>[http://scottchacon.com/2011/08/31/github-flow.html](http://scottchacon.com/2011/08/31/github-flow.html)
* Github pull requests<br/>[http://help.github.com/pull-requests](http://help.github.com/pull-requests)
* CCMenu<br/>[http://ccmenu.sourceforge.net](http://ccmenu.sourceforge.net)
* rbenv<br/>[https://github.com/sstephenson/rbenv](https://github.com/sstephenson/rbenv)
