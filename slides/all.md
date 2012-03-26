!SLIDE

# Deployment & Operations <br/>at PlayUp #

<br/>
### Ash McKenzie ###
#### March 27th 2012 ####

!SLIDE
  
# About me #

!SLIDE bullets

# Sports Data Team #

* Team of five, all in Melbourne
* Develop Sports Data API
* Process incoming sport XML
* Produce consistent RESTful JSON API

!SLIDE bullets

# Our clients #

<img src="playup-ios-logo.jpg" alt="PlayUp iOS logo" />

* PlayUp iOS app
* PlayUp Android app (coming soon)
* A number of internal R&D apps

!SLIDE bullets smbullets

# Our setup then #

<img src="horse-and-cart.jpg" alt="Horse and cart" />

* AWS based
* Lots of manual testing before deployment
* Production deployment once or twice a week
* Deployment was basic shell scripts
* Environments out of sync
* Devs had limited responsibility after commit

!SLIDE bullets incremental

# Our setup now.. #

* <img src="astro-boy.jpg" alt="Astro boy" />

!SLIDE bullets smbullets

# Development #

* AWS based
* Follow the 'Github flow' process<br/>(master branch always deployable)
* Jenkins CI performs all our tests (takes around 20 - 25 mins)

!SLIDE bullets smbullets

# Deployment #

* Deployment three to eight times a week
* Deployment is a push button affair
* Commit to deployment under 30 mins
* Deployments tagged and service description JSON dropped
* <img src="service-description.jpg" alt="Service description" />

!SLIDE bullets

# Future setup #

<img src="back-to-the-future.jpg" alt="Back to the Future" />

* Real-time sport events using PUB/SUB

!SLIDE bullets

# Thank-you! #
<br/>
## Links ##

* Github flow<br/>[http://scottchacon.com/2011/08/31/github-flow.html](http://scottchacon.com/2011/08/31/github-flow.html)