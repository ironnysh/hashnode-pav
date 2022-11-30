# The sysadmin diaries

#### Emanuel Stoi, Senior System Administrator and Project A’s Mac Guy in residence, talks about automation, tech support, the challenges of a hybrid workplace, and the importance of the human factor

![An article by Ronny Shani. Tech Content Writer at Project A — Berlin-based VC](https://cdn.hashnode.com/res/hashnode/image/upload/v1667896435735/DuiK9HgnU.png)

Project A’s Tech team is the company’s biggest group of operational experts. It includes back- and front-end developers, consultants and program managers, DevOps, and a content writer (👋), but the second-largest crew is the Sysadmins: A bunch of IT professionals responsible for everyone’s digital well-being.

The sysadmins handle all software and hardware installations, servers and infrastructure, networking, cybersecurity, compliance, and daily tasks related to running a hybrid workplace (Zoom Masters!).

“We have a very generalistic approach because it makes it easier to cover topics. When you get the workload we have, it makes sense to split responsibilities and ensure things get done even when some of us aren’t available”, says **Emanuel Stoi, Senior System Administrator**.

![A portrait of Emanuel Stoi, a senior sysadmin at Project A](https://cdn.hashnode.com/res/hashnode/image/upload/v1667896437125/imlPHdlEH.jpeg)
Emanuel Stoi. “I never imagined I’d have so much fun”

“Of course, our team includes people who specialize in certain things, like Michael Raeder (IT Compliance Manager — RS), who’s more focused on compliance, data privacy, and these topics. Otherwise, it’s everything from first-level support to preparing computers for newcomers to the most complex things — like maintaining our server infrastructure or automation. That’s probably the most high-level task, where we code like everyone else on the Tech team.”

\*\*Have things changed during Covid, when the whole company started working remotely?\*\*  
It was mostly about managing the people, not the infrastructure. Patrick (Patrick Salecker, Head of IT Infrastructure — RS) had designed it to be fully remote. The first thing we did was implement a VPN to monitor remote devices for security issues. Onboarding also became a bit more complicated, but we’ve since started using a central management system for Apple devices ([Jamf](https://www.jamf.com/)), so we can do the whole process remotely, even for the London office.

#### Have you tried turning it off and on again?

Contrary to what you may imagine when you think about sysadmins (socially-awkward dudes sitting in their solitary gaming-themed lairs?), Emanuel is empathic, attentive, and super-friendly.

\*\*You’ve been at Project A for four years — what’s your favorite part of the work?\*\*  
It’s hard to choose a favorite. First-level support and interaction with people are nice. I like doing onboarding presentations, and I enjoy helping people. I want it to be pleasant–not scary, where people feel someone orders them what to do. Of course, sometimes it can get annoying, like having to say the same thing ten times. That’s why we automate things.

That’s another favorite of mine, but you lack the human interaction: I could spend a week working on a project that nobody will ever know about–it will just happen in the background. You don’t get the same gratification when you work on automating a background process. It can be amazing and reduce a lot of work or annoyance, but very few people notice it; they sometimes assume it’s a message from Apple.

For example, I implemented a script that prompts people to restart their computers instead of waiting for them to reach out when they have issues. If they haven’t done a proper shutdown in the past ten days, they get a pop-up asking them to restart within two hours. While these preventive solutions are not as rewarding as helping someone fix a problem on their computer, this action actually resolved more than 50% of the issues.

**\*\*Do you prioritize these automation tasks? In other words, how many “**[**Have you tried turning it off and on again?**](https://www.youtube.com/watch?v=nn2FB1P_Mn8)” is too many?\*\*  
We have a virtual office day where we work together remotely and can spontaneously reach out to others with questions or problems. Sometimes someone gets annoyed — probably me most of the time — saying, ‘oh my God, I’m getting this question for the 10th time already. Can we do something about this?’ That’s when we start discussing a solution.

#### Compliance vs. autonomy

The ongoing work includes additional tasks: Maintenance, handling backlogs, and completing business-related assignments. “We have workshops where we align on bigger projects and a weekly call to discuss important projects or hot topics like tickets or ideas we need to plan. For example, I’m working on removing the admin rights of Mac users. I could create a super admin user and demote the normal users, but we want people to have the same user experience, so I’ve been building our own internal App Store using Jamf. Another feature automates system permissions, like screen sharing, so we don’t need to log in and use admin credentials.

![A screenshot of Project A’s in-house App Store. The capture shows the whole UI, with several app icons and a navigation bar on the left](https://cdn.hashnode.com/res/hashnode/image/upload/v1667896439055/fpWBhvqOE.png)
Emanuel’s App Store

\*\*How do you balance compliance, corporate guidelines, and security with giving people a sense of autonomy over their devices?\*\*  
That’s the biggest problem we’re confronted with because we don’t want people to feel like they’re now in a corporate environment where nothing’s allowed. We always try to give people an alternative, so they won’t feel like they lost something. There are some exceptional cases where there’s not a lot we can do to provide 100% compatibility, such as the recent blocking of personal Apple IDs. We can’t give you all the autonomy that you had before.

Our approach is to figure out things before they happen, just anticipate: What would I do? How would I react? What would people like to have? For example, we bought monitors with USB charging capabilities, so when people come to the office, they don’t need to bring their chargers or leave their stuff lying around.

Another example is not leaving unanswered help desk tickets. When someone writes to us via Slack or email, we engage on the same day. Even if we don’t provide an immediate solution, we interact to let them know we’re on it.

\*\*Would you say that your job requires psychological skills?\*\*  
There’s some social engineering and psychology involved. You might have seen my messages about upgrading apps or updating the OS, where I politely ask people to do the update. A few people do it every time I post a message, but not all. So after a few days, I will create a Slack group chat, a so-called *List of Shame*; I just write, ‘Hey, you are the last people who didn’t upgrade yet. Can you please do it as soon as possible? It takes a few minutes, and it’s crucial, so please do it.’ And then they will do it.

That’s the other side of giving people autonomy and control over their devices. It would’ve been so much simpler for me just to have a button and a cron job that checks the computer and reboots indiscriminately, without warning — even if you’re on a call. But instead, we’re going overboard to build mechanisms that slowly push people toward the goal instead of annoying them.

#### “I never imagined I’d have so much fun”

Hardly a classic Apple fanboy, Emanuel became the in-house Mac Guy by coincidence. “It happened incidentally for historical reasons: We had onboarding scripts for every operating system, and when we started using Jamf, I was the one who maintained those scripts and knew how to do that. My colleagues do this work as well — I’m just the one who does the most scripting. I’m a big fan of RPGs, and these big coding tasks are like mission or quest-driven video games. There’s a sense of accomplishment when you complete them”.

Speaking of scripting, Emanuel also manages Project A’s custom WordPress-powered intranet site and specializes in bash/PowerShell onboarding automation and Python programs that handle various other scenarios.

“After getting my master’s in Applied IT, I had a small business helping people with their computers. Meanwhile, I learned Java and JavaScript and planned to become a front-end developer. I applied to the sysadmin job because I thought it could be easy until I found a job as a developer. I never imagined I’d have so much fun because I get to experiment with many things: Testing new OS versions, figuring out solutions for problems, running multiple Docker containers, and comparing them to see which works best. I even get to play with a lot of toys, test devices and fix smartphones. It’s fun. Even when it sometimes feels like grinding work, in 99% of the cases, you still feel that there’s a positive result, and it’s more than great in the working environment”.

* * *

[The sysadmin diaries](https://insights.project-a.com/the-sysadmin-diaries-emanuel-stoi-b3b6620a9ea) was originally published in [Project A Insights](https://insights.project-a.com) on Medium.