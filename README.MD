#Session Title: Build quality in to automation#

#Brief Synopsis (c. 100 words):#
I often find that automation is a combination of scripts, code and dependencies that are very complex, inconsistent, not versioned and rarely hosted or packaged centrally, this can all be very brittle and introduce unacceptable risk. 

I will introduce, by example the benefits of building quality in to the automation code we write so as to address these issues, whilst providing a framework for collaboration. I will continue by discussing the separation of automation and orchestration concerns and how treating the build and deploy process as a first class citizen you can benefit product development, the team and the whole business.

#Talk Details: ##

##1. Setting the scene ##
*Timing: 0-2 mins (2 mins)*

####Purpose ####
Explain who I am, what this talk is about and what I mean by the terms build and deploy, automation and orchestration

* **Intro:** I'm Lloyd, I'm a freelance software engineer, I believe in #DevOps principles and strive to Continuously Deliver everything (even this talk..see https://github.com/Pipeline2016/README.MD). I've worked in many sectors including manufacturing, consultancy and eCommerce, in support, operational, development and more recently (last 7+ years) in a release/build/devops/consultancy capacity. 

* **Build:** The Commit phase of a common deployment pipeline, e.g. version, compilation, unit test and package for deployment later on.
* **Deploy:** Everything onwards of the Commit phase, i.e. automated and manual Acceptance, UAT and Live release.
* **Automation vs Orchestration:** I believe these are separate concerns, the area between the two is often blurred with much of the automation logic often creeping in to the orchestration process and tooling.
* **Containerization:** Specifics of this are out of the scope of this talk, however examples of this principle applied to containers can be found here: [TODO]() 

####The problem####
All too frequently I have observed that automation code and "processes" are a combination of very complex, unversioned locally saved code and dependencies. Delving deeper these important scripts are often rats nests of 100's or even 1000's of lines of logic, they're brittle, one change can break them or even worse give a non-deterministic output. Rarely do they implement consistent patterns for error handling, retry, auditing or security and idempotency is often not understood.

####Evidence####
* Demonstrate ugly scripts and brittle deploy processes

##2. Fail even earlier and debug locally##
*Timing - 3-7 mins (5 mins)*

####Purpose ####
Catch more failed builds earlier on by changing fewer variables, e.g. don’t compile and build in a completely different way on your Continuous Integration (CI) server than your developers do on their development machines.

* Building software is tricky, debug that locally so we don’t have to constantly break the CI builds and deployment processes to see things fail
* Debug and execute the exact same build/deploy scripts on your **developer workstation(s)** as you execute **on your build server(s)**, reducing surprises **when you deploy**

####Benefits####
* Promotes DevOps as a practice, CI, testing, delivery and Infrastructure as Code (IaC) become things everyone cares about and has visibility of.

####Evidence####
* Demo successful modular build running same code on dev desktop and one of TeamCity, AppVeyor, Jenkins etc.

##3. Make the build/deploy process a first class citizen##
*Timing - 8-12 mins (5 mins)*

####Purpose####
Put the build and deploy processes under version control and treat them as code, after all, we care about changes and versions of our product code… A LOT. 

* This is a software engineering problem, we should solve it as such
* No need to re-invent the wheel for every product/component
* Consistency, use convention over configuration

####Benefits####
* Increases productivity and code re-use, easily clone (or consume) the build/deploy process in to all application components 
* Stop using fragile UI's to hack in untracked scripts and logic
* Reusable, modularised components rather than nests of "automation scripts" 

####Evidence####
* Demo the previous successful modular build failing for a component and the workflow to fix and publish that change

##4. Improve quality##
*Timing - 13-17 mins (5 mins)*

####Purpose####
If we treat the build and deploy processes as code, then we can also test it as part of its own pipeline.

* Unit test coverage, version and package the build and deploy components. Dog fooding
* Integration testing is your build and deployment through lesser environments
* File bugs, prioritise effort, innovate, refactor, include within your technical roadmap/backlog

####Benefits####
* Grow your existing "helper" scripts in to quality proven code, production code if you like
* Collaborate as you would on product code, code reviews, pull/merge requests
 
####Evidence####
* Demo TDD with Pester and PowerShell that is driving our demo build process, show workflow and feedback loop

##5. Decouple automation from orchestration##
*Timing - 18-22 mins (5 mins)*

####Purpose####
The one thing that all vendors of build and deployment tools (TeamCity, TFS, Jenkins, AppVeyor, TravisCI, OctopusDeploy etc) have in common is they give you an inch, but allow you to take a mile. It is incredibly easy to use their out-the-box and add-on tasks, runners and plug-ins, however this means it is almost impossible to move to another technology or run a build in its entirety locally. Vendor lock-in is a very real result. 

* Decouple your build/deploy logic from the vendor of your CI and orchestration tooling
* Continue to use vendor supported tooling for orchestration
* Own your build/deploy logic (plus all benefits above)
* Run the same process everywhere

####Benefits####
* Decoupling benefits are understood well in software engineering, the same is true with orchestration, the landscape changes frequently and we should be able to adapt quickly and easily
* Tooling choices can be made more easily and with far less risk

####Evidence####
* Demo successful modular build running same code on developer/tester desktop and all of TeamCity, AppVeyor, Jenkins etc.

##6. Summary##
*Timing - 23-25 mins (3 mins)*

####Purpose### To summarise what we have talked about, the key points to takeaway and links to resources.

* Summary
	* **Who did that?** Lloyd Holman [@lloydholman](https://twitter.com/lloydholman)
	* **What happened?** I shared the benefits and advantages of treating your build deploy code and processes in the same way as your product code base, i.e as a first class citizen along with why we should decouple from big vendors and treat automation and orchestration as separate concerns. 
	* **Where and When did it take place?** Pipeline Conf, March 2016
	* **Why did that happen?** This is a topic close to my heart, I believe it allows us as an IT industry to live and breathe the DevOps mentality and ultimately add value by producing high quality build and deploy processes that can themselves be built upon and delivered in small batches to benefit product development for the business 

* Links to resources
  * [Original maturity model from the Continuous Delivery book]() - Credit to Pearson Education, Dave Farley [@davefarley77](https://twitter.com/davefarley77) and Jez Humble [@jezhumble](https://twitter.com/jezhumble) 
  * [This talk, with commit history](https://github.com/lholman/Pipeline2016/blob/master/README.MD)
  
###Talk notes###
* Agile: I believe in the agile manifesto and many of the Scrum/Kanban/Xanban/XP principles and applying them to one's organisation. That said, the single most important point, I believe, is an organisations culture being truly agile, actively encouraging early failure, efficiency and striving to reduce release batch sizes and time frames, this is key for enabling Continuous Delivery. 

* Continuous Delivery:  The CXX test, always be capable of deploying. Strong Continuous Integration (CI) with visible notifications and high quality output tested automatically. Deployment automation and configuration management governance. Fail ideas early, get to market before the competition and realise Return on Investment (RoI) quickly. Make code (app or infrastructure) packaged, integrated and deployable from the first committed line.

* What else can this approach enable during build or deploy phase?
	* Living documentation generation (PDF's from wiki)
	* Reporting on build
	* Change interrogation, feed in to deployment process?
	
###Length of talk: 25 mins###
