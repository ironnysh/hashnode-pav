# Unleash your inner SRE

In a fascinating essay published on the latest edition of [GitHub’s The ReadME Project](https://github.com/readme/guides/ops-work-visible), Lorin Hochstein, a senior software engineer at Netflix, explained the streaming giant’s software operations model, dubbed _You build it, you run it_.

> “The software engineers who write the services are also responsible for operating those services. This means they must be [full-cycle developers](https://netflixtechblog.com/full-cycle-developers-at-netflix-a08c31f83249), capable of doing both the development and operations work. This is different from the SRE model, where engineers who specialize in operations assume the responsibility of the operations work”.

![A red-haired woman coding in an office, sitting in front of a laptop connected to two screens](https://cdn-images-1.medium.com/max/1024/1*21y-gQJgUrI4weQxm_E_NA.jpeg)_When you’ve got ownership of the whole process, you see the big picture (Photo: ThisIsEngineering@Pexels)_

According to Hochstein, the benefit of Netflix’s approach is a streamlined software development life-cycle (SDLC):

> “Developers need to change the system to deliver features, so they want to make as many changes as possible. But every change carries a risk […] so operators want to make fewer changes. When the same engineers are responsible for both development and operations, they are in a better position to make tradeoffs between these conflicting goals”.

## Accountability and speed

When you enable every developer in your engineering team to deploy changes to the production environment, you stand to gain much more than a harmonious working environment.

1. Motivating people to participate in the entire process encourages them to **take responsibility** , contributing to greater accountability. They start to develop a feature or a bug fix and see it through to production. If the code they deployed breaks something, it’s their job to fix it.
2. They can **be independent**  — in terms of both time and knowledge: When only one person knows how to deploy, and they aren’t there, you’re out of luck. You might have a critical bug that nobody can fix. And it doesn’t matter which stakeholder is the gateway to the production deployment — it can be the product manager, DevOps, or any other relevant function in the company. When there’s no shared responsibility, a single person becomes a liability.
3. Finally, it allows you to **quickly push** code — whether bug fixes or new features. You don’t have to deploy according to someone else’s schedule or wait for some pre-planned deployment date that someone arbitrarily set.

## Break it till you make it

Of course, there are also downsides, mainly the risk of breaking something after deployment.

However, being responsible for the whole process can help minimize such scenarios. When a developer owns the workflow — from ticket to push — it means they contact QA once development is complete, get the feedback from QA, and either fix the problems or continue to the next stage, which traditionally would be DevOps’ domain. Now the developer is the person who takes care of that.

> Some teams come to a halt when they’re done coding and simply sit and wait for further instructions.

To say, “I’m only developing. Once it’s in QA, my work here is done”, means you abandon the thing you’ve worked on. But if the developer assigned to the ticket isn’t responsible, who is?

## Practice leadership

So what does it take to make people feel comfortable taking on this responsibility? As we’ve learned from supporting our portfolio companies, it’s not always a question of technical expertise. Sometimes the person who’s the gateway to production is the one who needs to change their mindset and be able to delegate and trust others.

Some companies are reluctant to adopt this practice. Citing seniority or familiarity with the codebase, they prefer the centralized approach. But it doesn’t guarantee fail-proof deployment because neither argument protects you from unexpected circumstances:

- Just because a person is familiar with the codebase doesn’t mean they’re never wrong; nobody is perfect, and everybody makes mistakes that cause unexpected bugs.
- When it’s a seniority consideration, it may result in poor risk management: What do you do if you have an emergency but the CTO (the only one who can deploy) is away for some reason?

Denying developers this broad-scoped responsibility toward the application or the ticket can sometimes produce poor results, whereas motivating them to feel more involved would improve code quality and increase productivity. We’ve seen teams come to a halt when they’re done coding, sitting there waiting for further instructions.

## Boost confidence

Some people worry about “breaking” the app, but that’s something that the team lead should mitigate: It’s their job to clear roadblocks and make everyone feel confident.

As a leader, you either create an atmosphere where everybody’s allowed to deploy, and it’s not the end of the world if something breaks because we can fix the problem, or you create a discouraging blame culture, where nobody will want that kind of responsibility.

> If you build something, you should ensure it works. That’s all part of the journey

It’s a chance for developers to face their fears: The more experience you have, the more comfortable you are, and the fewer mistakes you’ll make.

## Failure makes perfect

We would argue that even when something [does break in production](https://insights.project-a.com/to-roll-back-or-not-to-roll-back-how-to-handle-critical-incidents-in-production-4a7c99ef179c), and you can measure how much money you lost as a result — it’s still a good thing. That’s actually the point: If a developer can’t see the effects of their code changes and fails to notice this direct correlation, how can you feel responsible and accountable?

It may sound counter-intuitive, but when you think about it, the best-case scenario may be that you break something at some point. Assuming there are proper monitoring or alerting mechanisms (see below), you’ll quickly become aware of the problem, detect where the code you’ve just deployed failed, and take ownership of fixing it. Afterward, you can [discuss the issue](https://insights.project-a.com/post-mortems-dont-have-to-be-painful-439ca59190c5) in a retrospective, constructive way and do a [postmortem of the incident](https://sre.google/sre-book/postmortem-culture/).

What you do after the incident has been resolved is just as important as how you resolved it: You can deduce why it happened and how to avoid it in the future; you can see the direct consequence of your decisions.

## See the big picture

When you’ve got ownership of the entire process, you see the big picture: You know the codebase, you know what changed, and you understand how X relates to Y — how changing something at one place affects a seemingly unrelated layer.

An overview of the entire cycle boosts your productivity and performance.

![A screenshot of the Microsoft Azure Monitoring dashboard, displaying various colorful graphs and charts of the server infrastructure status](https://cdn-images-1.medium.com/max/1024/0*ZY9veuC-YZh5r0Mn)_“Implement monitoring tools — a dashboard where you see how your application works” (screenshot of Microsoft Azure Monitoring dashboard)_

Otherwise, developers are disconnected from reality. Their journey stops at the sandbox or staging environment because that’s the last thing they see; everything else happens under someone else’s eye — DevOps, sysadmins, or whoever else is responsible.

But if you build something, you should make sure it works. That’s all part of the journey.

## Mitigate the risk

As we said, there’s always the chance of breaking things when you deploy. Which tools and practices can you implement to lower the risk?

- **Share knowledge** of the codebase and the application’s functionality.
- **Familiarize the team** with the infrastructure: How many resources does it need? How many errors were there?
- **Incorporate QA** in your workflow.
- **Implement automated tests**  — at least manual checklist-based regression, unit, and integration tests.
- **Set up monitoring** tools — a dashboard where you see how your application works.
- **Give people access** to logs, monitoring, and pipelines (so they know what’s happening when something’s triggered).
- **Make the logs searchable** and filterable, and ensure every developer knows how to find the necessary data.
- **Notice business anomalies** and alert stakeholders. Let’s say that typically, your customers spend €4,000 from eight to nine in the morning. If today you had no transactions, the system will notify the relevant person.

## The manager’s perspective

[Stephan Schulze](https://www.linkedin.com/in/stephan-schulze/), Project A’s CTO, agrees that engineers should be able to deploy, given the proper safety net: Automation, testing, monitoring, etc. “It’s a process that requires pre-planning and risk management, but if a junior developer can deploy — you got it”.

He mentions that successful companies rarely operate in a centralized approach. According to the [DevOps Resource and Assessment (DORA) Accelerate State of DevOps 2021](https://cloud.google.com/blog/products/devops-sre/announcing-dora-2021-accelerate-state-of-devops-report) benchmark, teams that achieve exceptional operational performance deploy multiple times a day:

> “Elite performers continue to accelerate their pace of software delivery, increasing their lead time for changes […] to less than one hour. Not only that, but elite performers deploy 973x more frequently than low performers”.

This approach allows both startups and established companies to avoid bottlenecks, boost personal responsibility, and, most importantly, deliver value to customers (whoever they may be) much faster.

## Power to the people

“Developers may be a bit hesitant when it’s a large-scale or super-popular app where the stakes are higher, but I imagine that most will be interested in having the ability to deploy to production”.

Here’s what you can do to empower your team:

- Trust your people and make them feel confident and enabled.
- Implement tooling and procedures: [Automation](https://developerexperience.io/practices/automated-deployment), [testing](https://itnext.io/front-end-testing-strategy-5fddfd463feb), and monitoring. Assign code reviewers.
- Foster a positive [failure culture](https://www.toolbox.com/tech/devops/guest-article/how-a-culture-of-failure-can-make-your-dev-team-stronger/), where it’s okay to make mistakes as long as you have a process to fix them.

## Real-life scenarios

Offering examples that showcase an elaborate setup is outside the scope of this article. However, if you use Google Cloud Platform (GCP) or Microsoft Azure, it’s worth taking the time to read through their respective guides:

- [**GCP** ’s principles of operational excellence](https://cloud.google.com/architecture/framework/operational-excellence) “help build a foundation for reliability by setting up foundational elements like observability, automation, and scalability”: Learn how to [automate your deployments](https://cloud.google.com/architecture/framework/operational-excellence/automate-your-deployments) and [set up monitoring, alerting, and logging](https://cloud.google.com/architecture/framework/operational-excellence/set-up-monitoring-alerting-logging).
- **Microsoft Azure** ’s extensive documentation offers an [overview of alerts](https://docs.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview) and the company’s dedicated monitoring tool, [Azure Monitor](https://docs.microsoft.com/en-us/azure/azure-monitor/overview).

<small>_By [Stephanie Engel](https://www.linkedin.com/in/stefanie-engel/), Head of Technical Program Management@Project A_</small>

***

### Did you enjoy this story?
* Check out more stories on our [Tech Insights blog](https://insights.project-a.com/tech/home).

***