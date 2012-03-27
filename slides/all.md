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
* Switched to development as enjoyed creative aspect


!SLIDE bullets

<img src="playup-logo.png" alt="PlayUp logo" />

* Offices in eight countries
* We're obsessed with sport, ALL sport!
* We build applications and games around live sport
* Majority of development in Melbourne office
* Just released v2 of our iOS app
* Web app [http://beta.playup.com](http://beta.playup.com)
* Android app coming


!SLIDE bullets smbullets

# Sports Data Team #

* Five of us, all in Melbourne
* Develop Sports Data API
* Process incoming sport XML <br/>from five providers<br/>for nine sports<br/>with 54 leagues
* Constantly adding new sports and leagues


!SLIDE bullets

# Our clients #

<img src="playup-ios-logo.png" alt="PlayUp iOS logo" />

* PlayUp iOS app
* PlayUp Android app (coming soon)
* A number of internal R&D apps

ADD SCREENSHOTS


!SLIDE bullets

# Infrastructure #

* Importers
* API boxes
* Redundancy across regions / MySQL

!SLIDE

DIAGRAMS HERE


!SLIDE bullets smbullets

# JSON API #

* Consistent across all sports, RESTful and<br/>self discoverable
* Each sport, league, round and constest has a unique UID
* Utilises HTTP Accept header for versioning
* Rails based
* Use (and love) Varnish


!SLIDE

.notes some elements have been removed

# Sample JSON #

## Cricket contest ##


!SLIDE[tpl=code]

    @@@ javascript
    {
      ":self": "http://some.server.com/contests/20110159536",
      ":uid": "contest-20110159536",
      ":type": "application/vnd.playup.sport.contest.cricket.test+json",
      "scheduled_start_time": "2012-03-22T21:30:00Z",
      "start_time": "2012-03-22T21:30:00Z",
      "title": "New Zealand vs South Africa",
      "competition_name": "Test Cricket",
      "scores": [
        {
          "total": 1,
          "wickets": 0,
          "player": {
            "firstName": "Daniel",
            "lastName": "Flynn",
            "role": "batsman",
            "stats": "0(6)"
          },
          "striker": {
            "first_name": "Daniel",
            "last_name": "Flynn",
            "stats": "0(6)"
          },
          "non_striker": {
            "first_name": "Martin",
            "last_name": "Guptill",
            "stats": "0(7)"
          },
          "summary": "1/0",
          "team": {
            ":self": "http://some.server.com/teams/21",
            ":uid": "team-21",
            ":type": "application/vnd.playup.sport.team+json",
            "name": "New Zealand",
            "short_name": "NZ",
            "nick_name": "",
            "logos": {
              "header": [
                {
                  "density": "low",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_70x46.png"
                },
                {
                  "density": "medium",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_105x69.png"
                },
                {
                  "density": "high",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_140x92.png"
                }
              ],
              "calendar": [
                {
                  "density": "low",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_35x23.png"
                },
                {
                  "density": "medium",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_53x35.png"
                },
                {
                  "density": "high",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_new_zealand_nz_70x46.png"
                }
              ]
            }
          }
        },
        {
          "total": 189,
          "wickets": 3,
          "player": {
            "firstName": "Morne",
            "lastName": "Morkel",
            "role": "bowler",
            "stats": "0/0(1.1)"
          },
          "bowler": {
            "first_name": "Morne",
            "last_name": "Morkel",
            "stats": "0/0(1.1)"
          },
          "summary": "189",
          "team": {
            ":self": "http://some.server.com/teams/20",
            ":uid": "team-20",
            ":type": "application/vnd.playup.sport.team+json",
            "name": "South Africa",
            "short_name": "SA",
            "nick_name": "",
            "logos": {
              "header": [
                {
                  "density": "low",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_70x46.png"
                },
                {
                  "density": "medium",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_105x69.png"
                },
                {
                  "density": "high",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_140x92.png"
                }
              ],
              "calendar": [
                {
                  "density": "low",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_35x23.png"
                },
                {
                  "density": "medium",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_53x35.png"
                },
                {
                  "density": "high",
                  "href": "http://sdimages.playupgp.com/team-logos/cricket/cricket_south_africa_sa_70x46.png"
                }
              ]
            }
          }
        }
      ],
      "clock": {
        "overs": "2.1",
        "run_rate": "0.46",
        "last_ball": "0",
        "annotation": "play in progress",
        "summary": "Ov:2.1   RR:0.46   LastBall:0"
      }
    }


!SLIDE

# Setup #


!SLIDE bullets smbullets

# Past #

<img src="horse-and-cart.jpg" alt="Horse and cart" />

* AWS based
* Lots of manual testing before deployment
* Production deployment once or twice a week
* Deployment was basic shell scripts and a bit voodoo-esque
* Difficulty keeping environments in sync
* Devs had limited responsibility after commit


!SLIDE bullets incremental

# Present #

* <img src="astro-boy.png" alt="Astro boy" />


!SLIDE bullets smbullets

.notes Github flow master branch always deployable, 
  pull requests great for code review, 
  build lights are great - highly visible

# Development #

* Still AWS based
* Follow the 'Github flow' process
* Take full advantage of Github's pull request system
* Use git commit tags for clarity e.g. [api, db_schema]
* Jenkins CI performs all our tests
* Automated UAT deployment upon green light
* Use of build lights, CCMenu offline CI notifications


!SLIDE bullets 

# Production deployment #

* Shared / rotating role between team members
* From commit to production in under 30 mins
* Deployment is a push button affair
* Deploy three to eight times a week
* We deploy frequently so:
  * Deployed code is small and easily reversible
  * Stay as close as practical to our UAT env


!SLIDE bullets smbullets numbers

# Production deployment #

* Deploy sends email with git commit log
* Service description JSON dropped upon success
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

.notes RDS not used to cross region replication can occur,
Why Munin ?  No DB required, just Perl with RRDtool

# Technology #

* Ruby 1.9, PHP 5
* nginx, Passenger, Varnish
* MySQL (not RDS), Redis
* New Relic RPM, Munin, Nagios
* RVM (personally prefer rbenv)
* Capistrano, delayed_job


!SLIDE bullets

# OpsDev #

* Valuable being fully aware of environment
* Sharing deployment makes you think carefully about commits
* Ongoing invisible line of responsibility.  Good & bad.
* Personally feel more comfortable knowing entire setup


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
