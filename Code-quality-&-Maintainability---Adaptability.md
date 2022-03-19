Code Quality:
------------
Code quality is important for overall software quality.
The quality impacts how safe, secure, and reliable your codebase is.

Why?
===
1.Good Code Quality  code quality means that the code:
----------------------------------------------------
Does what it should.
Follows a consistent style.
Is easy to understand.
Has been well-documented.
Can be tested.

2.Testing Isn’t Enough
----------------------
Programmers aren’t perfect. Manual code reviews and testing will never find every error in the code.


3.Coding Errors Lead to Risk
-----------------------------
The quality of code in programming is important. When code is low quality, it might introduce safety or security risks. If software fails — due to a security violation or safety flaw — the results can be catastrophic or fatal.


4.Quality Is Everyone’s Responsibility
---------------------------------------
Quality is everyone’s job. The developer. The tester. The manager. High quality should be the goal throughout the development process.



Key Aspects to Measure
----------------------
Reliability
Reliability measures the probability that a system will run without failure over a specific period of operation.
It relates to the number of defects and availability of the software.
Number of defects can be measured by running a static analysis tool. 

Maintainability
Maintainability measures how easily software can be maintained.
It relates to the size, consistency, structure, and complexity of the codebase. 
Both automation and human reviewers are essential for developing maintainable codebases.

Testability
Testability measures how well the software supports testing efforts. 
It relies on how well you can control, observe, isolate, and automate testing, among other factors.

Portability
Portability measures how usable the same software is in different environments. It relates to platform independency.
It’s important to regularly test code on different platforms, rather than waiting until the end of development.
Enforcing a coding standard also helps with portability.

Reusability
Reusability measures whether existing assets — such as code — can be used again. Assets are more easily reused if they have characteristics such as modularity or loose coupling.

Reusability can be measured by the number of interdependencies. Running a static analyzer can help you identify these interdependencies.

How to Improve Code Quality?
----------------------------


1. Use a Coding Standard
-------------------------
Using a coding standard is one of the best ways to ensure high quality code.

A coding standard makes sure everyone uses the right style.
It improves consistency and readability of the codebase.
This is key for lower complexity and higher quality.

How to Do It
The best way to use a coding standard is to:
  Train your developers
  Help them to comply with it
 You can do this by using a static code analyzer.


2. Analyze Code — Before Code Reviews
-------------------------------------
Quality should be a priority from the very start of development. There isn’t always the luxury of time as development progresses. That’s why it’s important to analyze code before code reviews begin. And it’s best to analyze code as soon as it’s written.

In DevOps, code analysis takes place during the create phase. Static analyzers can be run over code as soon as it’s written. This creates an automated feedback loop, so developers can improve code before it goes to the code review phase.

After all, the earlier you find errors, the faster, easier, and cheaper they are to resolve.

How to Do It
The best way to improve quality is by analyzing code automatically. By running a static analyzer over code early and often, you’ll make sure the code that gets to the code review phase is the highest quality possible. Plus, you can use static analyzers (such as Helix QAC) to monitor key quality metrics.

3. Follow Code Review Best Practices
------------------------------------
Manual code reviews are still important for verifying the intent of the code. When code reviews are done well, they improve overall software quality.

How to Do It
The best way to do code reviews is to follow best practices and take advantage of automated tools. 


4. Refactor Legacy Code (When Necessary)
One way to improve the quality of an existing codebase is through refactoring. Refactoring legacy code can help you clean up your codebase and lower its complexity.

How to Do It
The best way to improve a legacy codebase is to do it gradually. Here are eight tips for improving legacy code (without compromising your software). 

There are several tools to measure the code quality. 
---------------------------------------------------
FindBugs (latest version 1.3.8) – uses static analysis to look for bugs in Java code. 
This is a great tool, it discovered possible NullPointerExceptions and a lot more bugs in our projects.

With the maven plugin you can do:
mvn findbugs:findbugs
which will use version 1.3.8 out of the box

PMD (latest version 4.2.5) – scans Java source code and looks for potential problems.
The rules are configurable, but at the beginning you will only need the provided one (and spend a lot of time to choose your favourites ;-) )In NetBeans 6.5 this tool is well integrated and works like a charme (CTRL+ALT+P).
With the maven plugin you can do:

mvn pmd:pmd
after you specified the following in the pom.xml under<reporting> <plugins> :

<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-pmd-plugin</artifactId>
  <version>2.3</version>
  <configuration>
    <targetJdk>1.5</targetJdk>
  </configuration>
 </plugin>
Other tools could be

JarAnalyzer – Is a dependency management utility for jar files. It’s primary purpose is to traverse through a directory, parse each of the jar files in that directory, and identify the dependencies between the jar files.

HammurAPI – a code quality governance platform

Best Code Review Tools In The Market
------------------------------------
Collaborator
Review Assistant
Codebrag
Gerrit
Codestriker
Rhodecode
Phabricator
Crucible
Veracode
Review Board

Maintainable code has several characteristics.
In general, code is said to be maintainable when it is all of the following:

Understandable – Someone else can pick up the code and figure out its purpose and general approach without a walkthrough by the original developer.
Intuitive – in the code just seem to make sense, no matter how complex the operation.
Adaptable – The code is written in such a way that variances in data don’t require a complete rewrite.
Extendable – Care has been given in the code architecture to allow extension of the core functionality in the future.
Debuggable – When something goes wrong, the code gives you enough information to identify the issues as directly as possible.


Adaptability:
-------------
Adaptability the extent to which a software system adapts to change in its environment.
An adaptable software system can tolerate changes in its environment without external intervention.

Eg: a dual-mode cell phone can find out by itself if any one of the two wireless standards it supports is avaliable at its current location and if so its starts using that standard.

Maintainability: How brittle the code is to change.
Reliability and testability are tied to maintainability since the only way a program is reliable (for a given env) is if it is kep running despite changes in its code, design, or even requirments.
eg. is the code rhoroughly regression tested? can modifications to the project be done in timely manner?

 