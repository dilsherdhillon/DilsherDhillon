---
title: 'How to git (hub)  '
author: "Dilsher Dhillon"
date: '2019-02-04'
image:
  caption: ''
  focal_point: ''
slug: how-to-git-hub
tags: []
categories: []
---

I think everyone at somepoint, regardless of what industry they're in, have folders which have files saved as _v2,_v3... v_final... That can only mean one thing down the line - chaos.   

I always though version control when it came to code was for a group of people working on a project, and for a lone statistician in the group as myself, I wouldn't need one. But, Jenny bryan's [Excuse me, do you have a moment to talk about version control](https://peerj.com/preprints/3159/) changed my mind.   

**So, what is a version control system, git for example?**  To quote Jenny   

"*Git is a version control system.  Its original purpose was to help groups of developerswork collaboratively on big software projects.  Git manages the evolution of a set of  les{ called arepositoryorrepo{ in a sane,  highly structured way.  It is like the \TrackChanges"  feature  from  Microsoft  Word, but  more  rigorous,  powerful,  and  scaled  up  to multiple files*"  

Why would a lone statistician need version control? For me, it's when I share analyis with collaborators, it's usually an interative process. Everytime you share a report, they'd like to see something new, a new graph/summary etc. Version control using git makes it easier to track in a sequential manner what was sent and what parts were updated.   

**So where does github fit in?** Again, to quote Jenny 
"*GitHub complements Git by providing a slick user interface and distribution mechanismfor Git repositories.  Git is the software you will use locally to record changes to a set of les.  GitHub is a hosting service that provides a Git-aware home for such projects on theinternet.  These relationships are shown in Figure 2.  GitHub is like DropBox or GoogleDrive, but more structured, powerful, and programmatic*"  


If you read her paper, I'm sure you will be convinced that you need git(hub) and will realize what you've missed out on so far.   

I'm going to quickly summarize the steps you need to creat a repository and start making commits to it!   

There are two ways to create a repository  
1. Create a new repository for a new project   
2. **Create a new repository for an existing project**   

I will be talking about the latter.   

If you're like me, the 2nd option is what was the most relevant for me since I had already ongoing projects that I needed version control on, and once you get the hang of that, creating new repos for new projects is easy.   

For either of these, you need to create an account at [github](www.github.com).   

Next, we have a project directory in our machines (MacOS in this case) called **Foo_Foo_Analysis**. We need to open up the terminal and change the directory to the **Foo_Foo_Analysis** folder ( for more go to [how to learn the command line](https://macpaw.com/how-to/use-terminal-on-mac))

``` bash 
cd ~/Foo_Foo_Analysis
```  

As a sanity check, I like to 
``` bash 
ls 
```
and make sure I'm in the right folder. 


Next, we want to *initialize a git repository IN THIS folder*  
``` bash
git init
```
Once this is done, we would like to add the files/folders under the repository to be tracked by git 

``` bash 
git add .
```  

And then we 
``` bash 
git commit -m"MY FIRST COMMIT WOHOOOOO"
```
The message after the quotes is essentially you telling your future self in a few words, what this commit was all about 

The last step is the *push* this repository, and since we want to use github for our version control, we need to go to github and   
1. Create a new repository - name the repo preferably the same name as your project folder, which in this case is **Foo_Foo_Analysis**     
2. Don't initialize Readme (just dont... You'll be able to add it later and it may save you a lot of headache)    
3. You should see this as an option     
``` bash
git remote add origin https://github.com/dilsherdhillon/foo_foo_analysis.git
git push -u origin master
```  
Go to the terminal and enter both of the above 



### And that's it  - you took your step in one of many more to come in version control using github!!  

Now simply go back to working on your project, working on those analysis, scripts etc and at the end of the day run these 3 simple lines 

``` bash 
cd ~/ToYourFolder
git add .
git commit -m "Whatever message you want to tell your future self"
git push

```
Now, if you were to start working on a new project, you could just create a new project directory in your local computer and run the above steps to start git(ting)!!! 





For more on how to use github for collobaroting on projects, pull requests etc, I would highly recommend reading [Jenny Bryan's](https://peerj.com/preprints/3159/) and also, if you're a R user, [this resource](https://happygitwithr.com/big-picture.html) will basically give you everything you need! 







