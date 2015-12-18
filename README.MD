#Session Title: One of the below#
Run the same build and deploy process everywhere
Debuggable builds
Build quality in to automation code
Automation vs Orchestration 
Quality pipelines

#Brief Synopsis (c. 100 words):#
All too frequently I have observed that automation scripts and "processes" are a combination of very complex, unversioned locally saved scripts. Delving deeper these important scripts are often rats nests of 100's or even 1000's of lines of logic, they're brittle, one change can break them or even worse give a non-deterministic output. Rarely are they idempotent.
To provide attendees with thoughts, ideas and proven examples of the benefits of separating the automation and orchestration concerns in software delivery. More specifically how applying this approach of making the build and deploy process a first class citizen within your deployment pipeline can benefit the whole product and team.

#Talk Details:##

##Set the scene##
*Timing - 0-2 mins (2 mins)*
*Purpose:* Explain who I am, what this talk is about and what I mean by the terms build and deploy, automation and orchestration, i.e. a more personal synopsis

* Intro: I'm Lloyd, I'm a freelance software engineer, I believe in #DevOps principles and strive to Continuously Deliver everything (even this talk..see https://github.com/Pipeline2016/README.MD). I've worked in many sectors including manufacturing, consultancy and eCommerce, in support, operational, development and more recently (last 7+ years) in a release/build/devops/consultancy capacity. 

* Build: The Commit phase of a common deployment pipeline, e.g. version, compilation, unit test and package for deployment later on.
* Deploy: Everything onwards of the Commit phase, i.e. automated and manual Acceptance, UAT and Live release.
* Automation vs Orchestration: I believe these are separate concerns, the area between the two is often blurred with much of the automation logic often creeping in to the orchestration process and tooling.
* Containerization: Specifics of this are out of the scope of this talk, however examples of this principle applied to containers can be found here: [TODO]() 

*The problem:* All too frequently I have observed that automation scripts and "processes" are a combination of very complex, unversioned locally saved scripts. Delving deeper these important scripts are often rats nests of 100's or even 1000's of lines of logic, they're brittle, one change can break them or even worse give a non-deterministic output. Rarely are they idempotent.

##Fail even earlier and debug locally##
*Timing - 3-7 mins (5 mins)*
*Purpose:* 

* Catch more failed builds earlier on by changing fewer variables, i.e. don’t compile and build in a completely different way on your Continuous Integration (CI) server than your developers do on their development machines.
* Building software is tricky, debug that locally so we don’t have to constantly break the CI builds to see things fail.
* Debug and execute the exact same build/deploy scripts on your.. **..developer workstation(s)** as you execute **..on your build server(s)** reducing surprises **..when you deploy**

*Benefits:* Promotes DevOps as a practice, Continuous integration, testing, delivery and infrastructure as code become things everyone cares about and has visibility of.
   
##Make the build process a first class citizen##
*Timing - 8-12 mins (5 mins)*
*Purpose:* Put the build and deploy processess under version control and treat them as code, after all, we care about changes and versions of our product code… A LOT. 

* This is a software engineering problem, we should solve it as such
* No need to re-invent the wheel for every product/component
* Consistency, use convention over configuration

*Benefits:* 
* Increases productivity and code re-use, easily clone (or consume) the build/deploy process in to all application components 
* Stop using fragile UI's to hack in untracked scripts and logic
* Reusable, modularised components rather than nests of "automation scripts" 

##Improve quality##
*Timing - 13-17 mins (5 mins)*
*Purpose:* If we treat the build and deploy process as code, then we can also test it as part of its own pipeline.

* Unit test coverage, version and package the build and deploy components. Dog fooding
* Integration testing is your build and deployment throughout environments
* File bugs, prioritise effort, innovate, refactor, include with your technical roadmap/backlog

*Benefits:* 
* Grow your existing "helper" scripts in to quality proven code, production code if you like

##Decoupled##
*Timing - 18-22 mins (5 mins)*
*Purpose:* I love TeamCity, have a long running tempestuous relationship with Team Foundation Server (TFS), have had a few flings with Jenkins  and chatted up various other CI and build servers/services, including but not limited to http://www.appveyor.com/, https://travis-ci.org/ and https://appharbor.com/. The one thing they all have in common (with the notable exception of https://appharbor.com/) is they give you an inch, but allow you to take a mile. It is incredibly easy to use their out-the-box and add-on tasks, runners and plug-ins, however this means it is almost impossible to move to another CI server technology or run a build in its entirety locally.

##Summary##
*Timing - 23-25 mins (3 mins)*

*Purpose:* To summarise what we have talked about, the key points to takeaway, links to resources and where we could improve.

* Summary
	* Who did that? 
		Lloyd Holman @lloydholman
	* What happened? 
		I shared the perceived benefits and advantages of treating your build and automation code and processes in the same way as your product code base, i.e as a first class citizen. 
	* Where did it take place?
		Pipeline Conf 2016
	* When did it take place?
		March 2016
	* Why did that happen?

* Links to resources
  * [Original maturity model from the Continuous Delivery book]() - Credit to Pearson Education, Dave Farley [@davefarley77](https://twitter.com/davefarley77) and Jez Humble [@jezhumble](https://twitter.com/jezhumble) 
  * [This talk, with commit history](https://github.com/lholman/Pipeline2016/blob/master/README.MD)
  
###Talk notes###
* Agile: I believe in the agile manifesto and many of the Scrum/Kanban/Xanban/XP principles and applying them to ones organisation. That said, the single most important point, I believe, is an organisations culture being truly agile, actively encouraging early failure, efficiency and striving to reduce release batch sizes and time frames, this is key for enabling Continuous Delivery. 

* Continuous Delivery:  The CXX test, always be capable of deploying. Strong Continuous Integration (CI) with visible notifications and high quality output tested automatically. Deployment automation and configuration management governance. Fail ideas early, get to market before the competition and realise Return on Investment (RoI) quickly. Make code (app or infrastructure) packaged, integrated and deployable from the first committed line.

* What else can this approach enable during build or deploy phase?
	* Living documentation generation (PDF's from wiki)
	* Reporting on build
	* Change interrogation, feed in to deployment process?
	
###Length of talk: 25 mins###