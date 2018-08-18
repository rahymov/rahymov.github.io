---
layout: post
title:      " CLI DAILY DEAL GEM"
date:       2018-08-16 22:18:05 -0400
permalink:  be_professional
---

Hello friends. I have created simple CLI gem daily deals on groupon. The first step is creating repository on github. Github.com click to new repository. Choose name for your gem make sure is not duplicate name.

On your mac terminal create gem.  It should be public repository. Reload your github page  will see your project. 

Then open your text editor or ide to see your project. On the terminal type atom . or sublime . to open your all project files.
First thing create daily-deal file on bin directory and add **#!/usr/bin/env ruby**. That terminal interpreter understand it is ruby file. 
To check it out if it is working or not  type on terminal bin/daily-deal and will see
 -bash: bin/daily-deal: Permission denied
Permission denied because file is not executable. Make file to executable cd bin and gonna get this:
daily-deal file is not executable you can see it. r(read) w(write) x(execute)
We need to change because user will interact with with daily-deal program.  After this steps could start programming your gem. First think about list of what need to do. Create cli file in the lib directory so you can start to coding. Create class and define methods that you woud use. On the **bin** directory create daily_deal file inside that file we would start our program.  During the coding were some challenges to but I watched the video and tried to understand(Thanks Avi). I did some research when get stuck. I had help from Kevin explained what was wrong when I can't solve the problem. Problem was I getting the deals and all instances collecting in one string. II have to iteration and problem would be solved.Now my program could list daily deals on groupon and when selecting deal shows title, original price, discount price, how many bought, ratings, product link. Of course program could be more complex and better than now. Hope one day will be. Happy coding:)


