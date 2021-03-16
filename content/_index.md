+++
title = "Online CodeRefinery Workshop and Hackathon on Software Testing"
+++

### March 17 and 24, 2021, 9:00-12:30 CET
<hr>

<p style="font-size:120%;"><i> Bring your code and start writing tests with the help of a mentor! </i></p>


### Registration
<a class="btn btn-danger disabled" href="#" data-mode="1" target="_blank">Registration is closed</a>

### Who the event is for

Are you doing any of these things?
- You write scripts to process data.
- You change scripts written by your colleagues.
- You write code that is used in research by you or others.
- You are not already extensively testing your code or scripts.

If yes, then the CodeRefinery testing workshop and hackathon is for you!

### Goals and format

In this event, you will become familiar with tools and best practices
for testing research software and get help in adopting these in your
own projects.

#### *Day 1: Workshop* 

Day 1 will be devoted to learning - we go through the [CodeRefinery
lesson on automated testing](https://coderefinery.github.io/testing)
and work on exercises in breakout rooms where you can use your
favorite programming language. <br>
<b>It is possible to only attend day 1 and not take part in the
hackathon.</b>

At the end of day 1, hackathon participants will be paired up with a
mentor and pitch their projects in small groups.

#### *Between Day 1 and Day 2*

In between the workshop and hackathon days you will get help from
your mentor to design tests, implement them in your code or set up
automated testing. Participants can communicate with mentors by email,
Zoom meetings or the [CodeRefinery
Zulipchat](https://coderefinery.github.io/manuals/chat/) and ask
questions. <br>
<b>You will be expected to spend at least 5 hours on
your project during this time.</b>

#### *Day 2: Hackathon*

During the hackathon on day 2, we split participants into groups and
they work in a sprint together with their mentor. At the end of day
2, we briefly summarize the progress made for each project and discuss
lessons learned.<br>

**Participants in teams will be together in a breakout room.**

### How to join

#### *Either A. Both workshop and hackathon, or B. Only workshop*

- There are two ways to attend: only workshop on day 1 or both
  workshop and hackathon on days 1 and 2.

- It is not necessary that all team participants choose the same
  option.

#### *Participation as a team* 

- If you collaborate with other people on writing code, we recommend
  that you all register to the event as a team. You can also sign up
  as a team even if you don't directly collaborate on coding.
- Teams will be working together in breakout rooms during the event
  and get paired with the same mentor. Team members should preferably
  use the same programming language.
- Decide a team name, and when registering, everyone enters this team
  name so that we can link you together. Note that everyone on the
  team must register separately.

#### *Participation as a single learner*

- Single learners are welcome! You don't have to write anything to the
  "team name" question in the registration form.
- During the exercise sessions in the workshop, 5-6 single learners
  are grouped into a breakout room to work together. Our instructors
  and mentors will be jumping around breakout rooms and answer any
  questions.
- However, please note that **hackathon participants in teams will get
  more mentor time than single participants.**

#### *To maximize benefit of the Hackathon*

- When registering, please write a description of the project you want
  to work on together with a mentor. Write what your code does, what
  language it's expressed in, whether it already has some tests, and
  what you would like to accomplish in the hackathon.
- To derive maximum benefit from the hackathon, we recommend that you
  make your code available in some form so that mentors can prepare.
- In the registration form you can provide a web address to your code
   repository if it's publicly available. If your code is not public,
   we will ask you to share it with a mentor before the hackathon.

### Prerequisites

- If you will attend the Hackathon, you are expected to bring a code
  project to the event in which you want to implement testing
  functionality. It does not need to be a large complicated codebase,
  just something you use or intend to use in your research. If it's
  not your own code, make sure that it has a license which allows you
  to modify it.
- You may need to install some software - see the Software
  Requirements section on below.
- It is somewhat important that you have a basic idea of how Git
  works. Please go through [this Git-refresher
  material](https://coderefinery.github.io/git-refresher/) for a basic
  overview and important configuration steps.

### Software requirements

You are assumed to have everything installed that you need for running
code in your preferred programming language, e.g. Python, Matlab or R
interpreters, or compilers for C/C++, Fortran, Julia, Rust, Go etc.

You also need to have a testing framework available for your preferred
language. Some languages need a package installation while others have
a framework built into their standard libraries. A list of recommended
tools and frameworks will be published here soon.

Other requirements:

- [Bash](https://coderefinery.github.io/installation/bash/)
- [Editor](https://coderefinery.github.io/installation/editors/)
- [Git](https://coderefinery.github.io/installation/git/)
- [Zoom](https://coderefinery.github.io/installation/zoom/)
- [Python and pytest](https://coderefinery.github.io/installation/python-testing/)
- [GitHub](https://github.com/) or [GitLab](https://gitlab.com/) account. 

Optional requirements depending on which language you will be using:

- C++ users will need [CMake](https://cmake.org/) and 
  [Catch2](https://github.com/catchorg/Catch2). Both can be installed through conda, 
  which you should have set up by following the "Python and pytest" installation 
  instructions above. In a terminal, run:  
  `conda install -c conda-forge cmake`  
  `conda install -c conda-forge catch2`  

- Fortran users will need to install [pFUnit](https://github.com/Goddard-Fortran-Ecosystem/pFUnit).
  pFUnit is supported on Linux and MacOS and is available on Windows through Cygwin. 
  Install pFUnit by following the 
  [official instructions](https://github.com/Goddard-Fortran-Ecosystem/pFUnit).

- R users will need [testthat](https://testthat.r-lib.org/). Follow the 
  instructions on the [official page](https://testthat.r-lib.org/).


### Schedule

#### *Day 1, March 17*
- 9:00 - 9:10
  Welcome and practical information
- 9:10 - 12:00
  [Software testing workshop](https://coderefinery.github.io/testing/)
  - 9:10 - 9:20
    [Motivation](https://coderefinery.github.io/testing/motivation/)
  - 9:20 - 9:30
    [Concepts](https://coderefinery.github.io/testing/concepts/)
  - 9:30 - 9:55
    [Testing locally](https://coderefinery.github.io/testing/pytest/)
  - 9:55 - 10:05
    Break
  - 10:05 - 10:45
    [Automatic testing with GitHub Actions or GitLab CI](https://coderefinery.github.io/testing/continuous-integration/)
  - 10:45 - 10:55
    Break
  - 10:55 - 11:50
    [Test design](https://coderefinery.github.io/testing/test-design/) 
  - 11:50 - 11:55
    [Conclusions and recommendations](https://coderefinery.github.io/testing/conclusions/)
  - 11:55 - 12:00
    Break
- 12:00 - 12:30
  Project pitching and introductory meeting with mentors (hackathon participants only)

#### *Day 2, March 24*
- 9:00 - 9:15
  Introduction
- 9:15 - 12:00
  Project work with mentors
- 12:00 - 12:20
  Presentations of progress made and lessons learned
- 12:20 - 12:30
  Final words and post-hackathon survey.


### Location

The hackathon will be held online, a Zoom link will be sent to accepted participants.


### Price and priority policy

Free of charge, funded by the [Nordic e-Infrastructure
Collaboration](https://neic.no/) and the [EuroCC National Competence
Center Sweden](https://enccs.se/).

When we have more sign-ups than our capacity allows, the following
priority criteria apply.

1. National universities or research institutes in Nordic countries
and Estonia
2. Private companies and government agencies in Nordic countries or
Estonia  
3. European national universities or research institutes from outside the Nordics.
4. Others

Therefore it is very important that you use an email address
corresponding to your affiliation.

### Instructors and mentors

- Anne Fouilloux
- Diana Iusan
- Johan Hellsvik
- Mark Abraham
- Qiang Li
- Radovan Bast
- Richard Darst
- Roberto Di Remigio
- Thor Wikfeldt


### Coordinators and hosts

- Naoe Tatara
- Thor Wikfeldt

### Helpers

- Samantha Wittke

### FAQ

- <b>Why should I join with a team?</b> If you will work together later,
  learning the tools at the same time is a great way to do it.

- <b>How does the waitlist work?</b> Anyone can register, but everyone goes to the waitlist. After the 3rd March, We'll continually approve people as we get space.

- <b>Does it matter where I work or study?</b> Because of the Nordic funding of
  CodeRefinery by [NeIC](https://neic.no/) and Swedish funding of
  [ENCCS](https://enccs.se/) we need to have a priority list described above. 



### Contact

support@coderefinery.org
