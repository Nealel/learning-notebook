# Problem Solving for Intermediate Developers

As Juniors, developers master certain modes of problem solving that are efficient for certain types of problems, but as they progress towards senior, there’s a shift in both the type of problems they are asked to solve, and the resources they have available to them. 

Intermediate developers likely have a good aptitude for problem solving already, but because they made pragmatic choices to get things done efficiently as a junior, they may lack experience with certain types of problem solving

This is a problem-solving guide intended for mid-level developers aiming to get to senior, specifically focused on solving technical problems like fixing tricky bugs. It may be useful for junior developers, too, but be aware that these juniors often have more efficient, effective options available.

## What changes from Junior to Senior?
| | Junior | Senior |
|-| ----------- | ----------- |
|Resources available|Can rely on others around to know the answers, and explain things to you.<p>A good junior doesn’t hesitate to ask questions, and makes full use of the expertise of those around them.<p>Often discouraged from spending too much time trying to work through something solo or going down a rabbit hole of irrelevant details because there’s simply too much for them to learn it all at once.|Faces problems no one else will know the answer to. <p>Is the expert in the systems they work with, so doesn’t have anyone to turn to to explain things<p>A good senior also makes full use of the expertise of those around them, but knows how to handle a problem when others can’t help them.<p>Often has no choice but to work through problems on their own, and has enough contextual knowledge to understand what’s relevant and what’s a rabbit hole.|
|Problem Difficulty|Faces common and simple problems that can be solved by using tutorials and copy-pasting code blocks from stack overflow. <p>A good junior knows how to use google, tech docs, and other resources to solve their problem quickly on their own|Faces unusual and complex problems that require a unique solution. Problem may involve specific interactions of multiple elements, or undocumented quirks of tools and libraries <p>A good senior knows how to go beyond the front page of google to build a deep understanding of the problem.|
|Problem Scope|Usually deals with well-defined requirements and clear problems with a right and wrong answer|Often must define their own requirements and deal with ambiguous problems. Relied on to make decisions, weigh trade-offs and make judgement calls.|

## Step by step guide

Most problem solving guides will tell you essentially the same steps: 
 1. Understand
 2. Theorize
 3. Test
 4. Repeat
 
 This guide is no exception.
 
### 1: Understand the problem:
  * Sometimes you can get lucky and accidentally find the solution by trying random things until something works. Trying things randomly can sometimes be the quickest solution to simple, common problems. You don’t need to understand how every little line of code works internally for every single problem you face. I’ve definitely been guilty of googling an error message and randomly copying whatever code’s in the top stack overflow answer without really reading it. But as the problems you face become more complex and less common, you need to know when it’s time to buckle own an put in the work to understand it. 
  * Often, if you understand the problem well enough, the solution will be obvious. This is the principle behind Rubber Ducking. When I studied philosophy, 80% of a typical essay would be spent properly understanding what was really meant by the question being asked, and once it could be phrased correctly, the problem would just dissolve, and I’ve found this applies to many things in life.
 * Take your time here. Building a good understanding of the problem takes time up front, but saves time later. And beyond just this problem, the in-depth learning you do now is a long-term investment that will pay off later.
 * Techniques
    * We often think we understand more than we do, and it's only when we try to explain it to others that we realize the limits of our understanding. Use Rubber Ducking, or my favourite modern alternative, the unsent slack draft. Write up a slack message to a coworker asking for help with the problem (ideally, pick a less-than-helpful coworker or a public slack channel that will incentivize you to put together a really clear write, thorough up). In your message, explain exactly what you know about the problem clearly and concisely. Include a run-own of what you’ve already tried, what you think the problem could be, and what you don’t know. You’ll often find in the process of writing it up there’s a way forward you didn’t see before, something you should have tried but haven’t. This brings us to the second step, Make a Theory.
    * Read the damn docs. And read the source code, too. Get comfortable with to clicking through and see how that library you imported is actually working internally. If you’ve been stuck on this problem for a while, take your time to read and really absorb information to fill in the blanks of your understanding.
    * Ask others to help you fill in different pieces of the puzzle. Being a senior often means needing to gather the information you need from several different experts in several different topics, and synthesizing it to see the whole picture of your problem.

### 2: Make a theory
  * Now you understand the problem, you hopefully have at least one, but maybe several ideas for what you can investigate.
  * How to prioritise which theory to investigate first? There are a few strategies:
    * Most likely first. If you’ve got a hunch, follow the hunch.
    * Most informative first. Which theory narrows the problem the most? If you’ve got a sequential process that has 10 steps, if you’re able to test if the problem happens before or after step 5, that cuts the problem space in half.
    * Easiest to test first. If you can test one theory in 10 minutes and the other will take a day, go for the one that takes 10 minutes first.
  * If you don’t have a theory
    * Bring in others. Even if they don’t know the answer, they might have ideas or hunches or questions that give you something to explore.
    * Take a break. Let the problem rest and go do something else. Walk the dog, take a shower, work on something else for a few days. It might come to you.
    * Revisit step 1. Your understanding of how things should work clearly doesn’t match how they do work in reality, so where is the gap?

 ### 3: Test the theory
  * Test one thing at a time. A single theory, a single variable. Testing multiple things at once can just lead to confusion. Testing one thing at a time can be harder than it seems, so be mindful if confounding variables are sneaking into your test
    * Avoid changing code while a test is running. It can be tempting to start writing the code to test the next theory, but this can create a lot of confusion if you lose track of exactly what code you were testing. Besides, if you are tempted to edit code, your testing loop is probably too long, which brings me to the next point
  * Get a good testing loop. This isn't optional. The time between finishing writing the code that tests the theory and getting the result of that test shouldn’t be long enough to get distracted by checking your email. The difference between an integration test that takes 1 minute to run, and a build-deploy-manually-test cycle that takes 30 minutes is 30x (or once you factor in all the distraction and context-switching that comes with a 30 minute delay, it’s more like 50x). That means that one hour's worth of tests using the integration testing framework is over 6 working days of tests using the build-deploy loop.
    * If your systems aren’t set up for easy testing, getting a good testing setup can take a time investment, but it’s an investment that will pay off again and again. The majority of times I’ve seen a bug that seems impossible to solve and drags on and on, it’s been something with a slow testing loop.
  * If necessary, keep notes. Some problems slipperier than others. If you find yourself saying “I swear I tested this earlier and got a different result”, it’s time to start taking methodical notes of exactly what you tested, how and what the result was. A great way of doing this is to create a new git branch and commit code after every test, including the test result in the commit message.

 ### 4: Repeat if necessary
  * If you haven’t found the problem, then you should have at least gained some new information from the test. Hopefully you can rule something out and narrow on where the problem is. Maybe your understanding has radically changed, or you’ve found a gap in your knowledge that needs to be filled. Go back to step 1 and update your understanding with this new knowledge.

### But also, step 0, be practical:
* You don’t need to solve every problem you encounter, and you definitely don’t need to solve every problem the “right way”. If a problem is dragging on for longer than it should, take a serious look at your options. Are there any workarounds? Is this a bug you can live with? Look at all the options, and weigh up the consequences of each
* Use the expertise of the people around you to the fullest. This is almost always more efficient than trying to go it alone. And even if no one around you knows the answer, collaborating on the above steps to solve it together can still be must faster than doing it alone.
