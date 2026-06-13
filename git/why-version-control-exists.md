# Why Version Control Exists: The Pendrive Problem

Originally published on Hashnode:

https://devintelligence.hashnode.dev/why-version-control-exists-the-pendrive-problem

---

1.WHAT IS THE MAIN PROBLEM ?

Let's understand with a real life imaginable scenario.

Imagine it’s 2005, and you’re a developer building a college management system.At first, the project is small. You create a folder named “College_Management_System” and start coding.After a few days, you add a new feature but are afraid something might break. Instead of using version control, you simply make a copy of the folder and rename it:





College_Management_System



College_Management_System_Final

A week later, you add another feature and create another backup:





College_Management_System



College_Management_System_Final



College_Management_System_Final_v2

A month later, your folders look like this:





College_Management_System_Final



College_Management_System_Final_v2



College_Management_System_Final_v3



College_Management_System_Latest



College_Management_System_Latest_Final



College_Management_System_Really_Final

Now comes the problem.

One day, your professor reports a bug. You remember that the application was working perfectly two weeks ago, but you have no idea which folder contains that version. Was it Final_v2? Final_v3? Or Latest_Final?

You start opening folders one by one, trying to find the correct version. What should have taken a few seconds now takes hours.

Sharing Code Through Pendrives

Suppose you are working on a project with your friend Rahul.

You complete the login module and save the project on a pendrive. The next day, you give the pendrive to Rahul so he can work on the attendance module.

While Rahul is making changes, you continue improving the login module on your own laptop.

After two days:





You have Version A



Rahul has Version B

When Rahul returns the pendrive, both versions contain different changes.

Now someone has to manually compare files and merge the changes. If either of you accidentally replaces a file with an older copy, some work may disappear forever.

This was one of the biggest problems with the pendrive approach: there was no safe way to combine changes made by multiple people.

Sharing Code Through Email

Email was another common solution.

Imagine your team consists of three developers:





You



Aditya



Karan

You finish some work and email the project:
Subject: Project_Final.zip

Aditya downloads it, adds a feature, and sends:
Subject: Project_Final_v2.zip

Karan downloads an older email by mistake and sends:
Subject: Project_Final_Updated.zip

Now the team has three different versions of the same project.

Nobody knows:





Which version is the newest?



Which version contains all features?



Which version should be deployed?

Developers spend more time managing files than writing code.

This is the beginning of the Pendrive Problem.

The “Pendrive Problem” is not an official technical term. It’s a simple way to describe the problems developers faced before version control systems like Git existed, when they used pendrives, emails, and copied folders to manage code.

SUMMARIZE THE PROBLEM





Overwriting Code Imagine two people are working on the same file. Person A edits the login function. Person B, working from an older copy, edits the signup function in the same file — but their copy doesn’t have Person A’s changes yet. When Person B copies their version back, it completely overwrites Person A’s file. Person A’s changes to the function? Gone. Nobody did anything “wrong” exactly — there was just no system to combine both sets login of changes safely.



Losing Changes Since everything depended on manually copying folders around, a single mistake — copying the wrong folder, overwriting a newer version with an older one, or a pendrive randomly corrupting files — could wipe out hours or even days of work. There was no “undo” button for this. If you didn’t have a separate backup of that exact version, it was simply gone.



No Collaboration History Even when things didn’t break, there was another problem: nobody could answer simple questions like: “Who changed this part of the code?” “When was this feature added?” “Why was this line removed?” “What did this file look like last Tuesday?” With folders and pendrives, there’s no record of who did what and when. Every change just silently replaces the previous one, with no trail left behind. Here’s what that “no history” situation looks like — multiple developers editing the same file, with no record of who changed what or when?



Difficult Team Collaboration As team sizes increased, manually merging code became almost impossible.



No Easy Rollback If a new change introduced a bug, developers had no reliable way to return to a previously working version



we saw what was the problem?

Now we are feeling that we need a strong tracking tool,why? As software projects became larger, the old methods of managing code started breaking down.

A single developer might be able to manage a few folders named Final, Final_v2, or Latest_Final. But what happens when a project has 10, 50, or even hundreds of developers working on it simultaneously?

Imagine a team building an e-commerce website. One developer is working on the login system, another is adding the shopping cart, while a third is integrating payment gateways. Every day, dozens of files are being modified.

If everyone exchanged code through emails and pendrives, the team would constantly face questions like:





Which version is the latest?



Who changed this file?



Why was this code modified?



How do we combine everyone’s work?



What if a new change breaks the application?

The bigger the team became, the bigger these problems became.

Developers needed a system that could automatically track every change, maintain a complete history of the project, and allow multiple people to work on the same code without overwriting each other’s work.

This need gave birth to Version Control Systems (VCS).

2) Let's look at the solution now

Verison control system

Version Control System (VCS)

The problems caused by pendrives, emails, and folders like Final, Final_v2, and Latest_Final eventually became too difficult to manage.

Developers needed a better way to keep track of their code, collaborate with teammates, and safely recover previous versions when something went wrong.

This led to the creation of Version Control Systems (VCS).

What is a Version Control System?

A Version Control System (VCS) is a tool that records every important change made to a project over time.

Think of it as a time machine for your code.

Instead of creating dozens of folders such as:





Project_Final



Project_Final_v2



Project_Final_v3



Project_Latest_Final

a VCS automatically stores every version of your project in an organized history.

Whenever you make a meaningful change, the VCS saves a snapshot of your project. If something breaks later, you can easily return to an earlier working version.

Now connect with some examples.

Imagine you are writing a book.

On Monday, you write Chapter 1.

On Tuesday, you add Chapter 2.

On Wednesday, you rewrite Chapter 1, but later realize the old version was better.

Without a VCS, the original chapter may be lost forever.

With a VCS, you can simply go back to Monday’s version and restore it within seconds.

This is exactly how a Version Control System works for software projects.

Another Example: Team Collaboration

Suppose three developers are working on the same project:





Aditya is building the Login page.



Karan is working on the Dashboard.



You are integrating Payments.

Without a VCS, everyone would exchange ZIP files, emails, or pendrives, making it easy to overwrite each other’s work.

With a VCS, everyone can work on their own changes independently, and later combine them safely into a single project.

let's summarize some benfits





Tracks Every Change
Every modification made to the project is recorded.





What changed



Who changed it



When it was changed





Restores Previous Versions Easily
Made a mistake?
Accidentally deleted an important file?
A VCS allows you to return to an earlier version of the project without losing everything.



Makes Team Collaboration Easy
Multiple developers can work on the same project simultaneously without constantly sending files to each other.



Prevents Accidental Overwrites
A VCS helps manage changes from different developers and reduces the risk of one person’s work replacing another’s.



Maintains a Complete Project History
Every version of the project is stored in a timeline.
You can travel back and inspect any previous state of the project whenever needed.



Acts as a Backup System
Even if your computer crashes or a file is accidentally deleted, the project’s history remains available.



Enables Experimentation Without Fear
Want to try a new feature?
A VCS allows developers to experiment freely because they can always return to a stable version if things go wrong.



Improves Accountability
Every change is associated with the developer who made it. This makes project management, debugging, and code reviews much easier.



3) How GIT and GITHUB comes in picture?

we saw, A Version Control System solves the problem of tracking changes and managing project history.

Today, the most popular Version Control System is Git.
In 2005, the development of the Linux operating system faced a version control challenge.

The Linux kernel was being developed by thousands of contributors around the world, and the existing tools were no longer meeting their needs.

To solve this problem, Linus Torvalds created Git.

Git is a distributed version control system that helps developers track changes in their code, maintain a complete history of a project, and collaborate with others without overwriting each other’s work.

In simple terms, Git acts like a smart record keeper that remembers every important change made to a project.

As software development became more collaborative, developers also needed a way to store their Git repositories online and work together from different locations. This led to the rise of GitHub.

GitHub is a cloud-based platform built around Git. It allows developers to store repositories online, share code with others, collaborate on projects, review changes, and contribute from anywhere in the world.





Git tracks and manages changes in your code.



GitHub helps you store, share, and collaborate on Git repositories online.

In one line , see the difference:

GIT is a local software and GITHUB is a cloud platform

Together, Git and GitHub have become essential tools in modern software development.

SOME DIAGRAMS FOR BETTER UNDERSTANDING



4)CONCLUSION

Today, it’s easy to take Git and GitHub for granted. We run a few commands, push our code, and collaborate with developers across the world without thinking much about it.

But before Version Control Systems existed, software development was far more chaotic.

Developers relied on pendrives, emails, and countless folders named Final, Final_v2, and Latest_Final to manage their projects. As projects grew and teams became larger, this approach led to overwritten code, lost changes, confusing file versions, and collaboration nightmares.

The real problem was never the pendrive itself. The problem was the absence of a reliable system to track changes, preserve history, and coordinate work between multiple developers.

Version Control Systems solved this challenge by introducing a structured way to manage code. Git took that idea further by making version control fast, distributed, and developer-friendly. GitHub then made collaboration possible on a global scale.

The next time you create a commit, switch a branch, or push code to GitHub, remember that these tools exist because developers once struggled with the very problems we’ve discussed throughout this article.

Git and GitHub are not just tools—they are solutions to a problem that software development could no longer ignore.

And it all started with the simple question:

“Which version of the project is the correct one?”

