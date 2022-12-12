# Say goodbye to dependency hell, supply chain attacks, and performance issues

**_Contributing editor: [Juan Pablo Denis Otárola](https://www.linkedin.com/in/jpdeniso/)_**

Without looking, how many times have you typed `npm install` this week? For the sake of our little game of stats, you can also replace this particular `CLI` command with `composer require`/`yarn add`/`pip install`/`gem install` - whichever juices your development environment.

In its [Octoverse 2020’s report](https://octoverse.github.com/static/github-octoverse-2020-security-report.pdf), GitHub found that JavaScript has the highest number of median dependencies, followed by Ruby, PHP, Java, .NET, and Python. When it comes to non-direct dependencies, the gap was baffling: 683 in JavaScript, 70 in PHP, and only 19 in Python. We’ll get back to the why in a second.

According to the same report, npm - **_The_** JavaScript package manager - has the highest percentage of references in [GitHub’s Advisory Database](https://github.com/advisories?query=type%3Areviewed+ecosystem%3Anpm) and the highest number of critical and high-severity advisories. But while the [most commonly used](https://insights.stackoverflow.com/survey/2021) programming language is also the most vulnerable, PHP, Python, or Ruby package managers aren’t a haven where developers can merrily relinquish control.

### The sequoia-wide dependency tree

Now’s the time for the explanation we promised. GitHub attributes the gap to:

> “npm’s philosophy of ‘micropackaging’ (packaging even one-liner functions as dependencies) \[...\] Micropackages are rarely used in applications (i.e., as direct dependencies) but commonly used in libraries, so they show up as transitive dependencies.”

The [2019 State of Software Supply Chain](https://www.sonatype.com/hubfs/SSC/2019%20SSC/SON_SSSC-Report-2019_jun16-DRAFT.pdf) report came to a similar conclusion, and [npm’s 2018 annual report even found](https://medium.com/npm-inc/this-year-in-javascript-2018-in-review-and-npms-predictions-for-2019-3a3d7e5298ef) that

> “the average modern web application has over 1,000 modules, and trees of over 2,000 modules are not uncommon. In fact, 97% of the code \[...\] comes from packages downloaded from the npm repository. An individual developer is responsible only for the final 3% that makes their application unique and useful.”

![Dependency hell: A drawing of an elaborate, fragile structure illustrating modern software infrastructure. By Randall Munroe@xkcd.com](https://cdn.hashnode.com/res/hashnode/image/upload/v1655392899424/uuRGunPoj.png  align="center")
*[License](https://xkcd.com/2347): Randall Munroe@xkcd.com, CC BY-NC 2.5*

In short, requiring a package for every trivial task leads to a lush, Sequoia-wide dependency tree that might bury you under it.

### The crash pad

The `left-pad` package, released in 2014, solved a common challenge: Adding characters to the beginning of a string with a single little function:

```
function leftpad (str, len) {  
var i = -1;  
len = len - str.length;

while (++i < len) {  
str = ' ' + str;

}  
return str;  
}
```

Back then, when neither browsers nor `Node.js` offered built-in support for this functionally, left-pad was picked up as a dependency of [another now-deprecated](https://www.npmjs.com/package/line-numbers) package (20 lines of code; 15K weekly downloads) incorporated into major tools, including Babel and React.

Fast forward to March 2016, when the developer, Azer Koçulu, decided to unpublish `left-pad` along with his entire npm catalog (273 packages in total), following a dispute over trademarks and free software. His protest caused a chain reaction: While npm contained the incident within less than three hours, [it recorded](https://blog.npmjs.org/post/141577284765/kik-left-pad-and-npm)

> “hundreds of failures per minute, as dependent projects failed when requesting the now-unpublished package.”

Today, [the deprecated package](https://www.npmjs.com/package/left-pad) has close to 3 million weekly downloads and +500 dependents, ignoring the prominent warning that recommends developers use the widely-available [built-in method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) `String.prototype.padStart()`.

### Appetite for Destruction

Since we began to work on this article, over 1,500 malicious packages have hit the world’s favorite package manager, targeting Azure, Kubernetes, Node.js, React — you name it. [Apparently](https://checkmarx.com/blog/a-beautiful-factory-for-malicious-packages/), a single actor — _RED-LILI_ — is responsible for this widespread **_typosquatting_**: Publishing malicious packages with names similar to legitimate ones, hoping that people accidentally misspell when they type `npm install <package>`.

RED-LILI’s contribution to the history of malware is adding a touch of automation: Security experts who analyzed the packages to track down the authors traced them back to the same person, who’s [been busy publishing](https://gist.github.com/Aviadg/3e640afe6dcbc651958c270ff9e57c8d) since November 2021.

> Reaching for a library when all you need is one method — is misguided

Another developer, Brandon Nozaki Miller (aka, RIAEvangelist), gained wider notoriety last month when they [injected malicious code](https://gist.github.com/MidSpike/f7ae3457420af78a54b38a31cc0c809c) into their npm package, [`node-ipc`](https://github.com/RIAEvangelist/node-ipc). The package — used in popular tools like Vue CLI and Unity Hub — targeted people in Russia and Belarus and overwrote the contents of their file system with a heart emoji.

This so-called _protestware_ was live for less than 24 hours, but with over a million weekly downloads, it became a major incident. RIAEvangelist soon dropped a new release, which imports a module named [`peacenotwar`](https://github.com/RIAEvangelist/peacenotwar) — a [multilingual call for world peace](https://github.com/RIAEvangelist/peacenotwar/blob/main/WITH-LOVE-FROM-AMERICA.txt) and responsible code architecture:

> “If you do not like what this module does, please just lock your dependencies \[…\] Also, please code-review your other modules for vulnerabilities.”

As of this writing, `node-ipc v11.1.0` received over 900k weekly downloads and has close to 1.3k stars on GitHub.

### A bundle of joy

Front-end developers may feel immune, protected under the cape of a brawny bundler that prevents them from spreading evil. But there’s another reason they should reconsider their approach to dependencies: Performance.

Trimming the dependency fat is your best bet for [optimization](https://itnext.io/a-case-study-of-a-react-pwa-performance-optimization-5e7bf26acffb) and boosting an app or a website’s performance. `Moment.js` is a good example: Even the maintainers of this +4MB library advise [against using it](https://momentjs.com/docs/), but over 20 million weekly downloads indicate not many are listening.

![Animated GIF showing an interactive treemap visualization of the contents of software bundles (Source: Webpack Bundle Analyzer)](https://cdn.hashnode.com/res/hashnode/image/upload/v1655392901726/qWT0UlWHb.gif)
*“An interactive treemap visualization of the contents of all your bundles” (Source: [Webpack Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer))*

**_Project A_**’s front-end team has been gravitating toward that direction for a while, simply because their holy grail is a perfect Lighthouse score. If that’s your goal, reaching for a library when all you need is one method is misguided.

And it’s not just the end-users; performance issues trickle down all the way to individual developers: “Adding many large dependencies tends to slow down install times significantly and make all operations slower for everyone globally”, warns Christoph Nakazawa, former Engineering Manager at Facebook, in an [extensive guide](https://cpojer.net/posts/dependency-managers-dont-manage-your-dependencies) on handling third-party dependencies.

As one of the developers behind `Yarn`, you better believe Nakazawa when he says, “Existing JavaScript dependency managers are actually not very good at managing dependencies.”

### Tips, best practices, and resources

What can you do to curb security issues, escape dependency hell, and improve performance? **_TL;DR_**: Investigate, review, and then investigate some more.

1.  **Npm Registry is a starting point** — thoroughly review potential packages and go beyond the obvious: Inspect GitHub issues (and note how many are open), browse through the commits history, and check for badges that confirm the latest release passed build tests.
2.  **Don’t be star-struck** — a project’s number of stars or weekly downloads indicates its popularity — not security or efficiency. Better metrics are pull requests, documentation (preferably more extensive than a `README` file), and even Stack Overflow mentions.
3.  **Avoid abandonware** — if you see a bunch of old, unmerged pull requests, consider looking elsewhere. Check the dates of the last merges or releases, and make sure they’re recent.
4.  **Guard the lockfile** — Lockfiles guarantee installations remain identical and reproducible throughout the development pipeline, across users and systems. However, malicious actors can still manipulate dependencies by pushing minor and major versions (Snyk’s security experts [posted a proof-of-concept](https://snyk.io/blog/why-npm-lockfiles-can-be-a-security-blindspot-for-injecting-malicious-modules/) following a deviously clever example of such manipulation), so stay vigilant.
5.  **Automation with a touch of manual oversight** — in the [_Tao of Node — Design, Architecture & Best Practices_ book](https://alexkondov.com/tao-of-node/#pin-dependency-version), software engineer Alex Kondov recommends eschewing semantic versioning in favor of pinned versions and manual audit and update cycles. Adopting this approach might sometimes be unrealistic and eventually detrimental since keeping dependencies up-to-date is crucial as it is time-consuming.  
    Automated tools like [`Dependabot`](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates) or `npm-check-updates` (`NCU`) can help: `NCU` streamlines upgrades, supports selectively updating modules and [has a Doctor Mode](https://github.com/raineorshine/npm-check-updates#doctor-mode) to test breaking changes.

#### Security Resources

*   You can track known security vulnerabilities via the [**CVE Program’s online database**](https://www.cve.org/). Type in the CVE ID and get information about publicly disclosed cybersecurity vulnerabilities.
*   GitHub has recently open-sourced its [**Advisory Database**](https://github.com/advisories), allowing anyone to contribute insight and intelligence on security vulnerabilities.
*   Snyk offers a handy resource titled [**_Cheat Sheet: 10 npm Security Best Practices_**](https://snyk.io/blog/ten-npm-security-best-practices/), including code snippets, tips, and rules-of-thumb.
*   [Socket](https://socket.dev/) is a new player that offers an attractive proposition: **Block supply chain attacks** by detecting dozens of red flags and monitoring dependency changes in real-time.
*   **Scopes and private registries** — [GitHub’s guide offers](https://github.blog/2021-02-12-avoiding-npm-substitution-attacks/) ways to tackle npm typosquatting attacks in private registries. [Microsoft has a similar white paper](https://azure.microsoft.com/mediahandler/files/resourcefiles/3-ways-to-mitigate-risk-using-private-package-feeds/3%20Ways%20to%20Mitigate%20Risk%20When%20Using%20Private%20Package%20Feeds%20-%20v1.0.pdf) with tips for Maven, NuGet, pip, and Gradle.

#### Performance Resources

*   [**NPMCompare**](https://npmcompare.com/) provides a detailed comparison of npm packages, including dependencies, open issues, pull requests, etc. NPMCompare rates each package based on the community and maintenance.
*   [**Bundlephobia**](https://bundlephobia.com/) analyzes a package’s size, download time, composition, and sizes of individual exports. It lets you research specific versions and links to similar packages. A bit buggy, but still valuable.
*   [**Webpack Bundle Analyzer**](https://www.npmjs.com/package/webpack-bundle-analyzer) generates a graphical representation of all your dependencies and helps pinpoint potential optimization opportunities.

***
#### Did you enjoy this story?

- Check out more stories on our [Tech Insights blog](https://insights.project-a.com/tech/home)
***
[Say goodbye to dependency hell, supply chain attacks, and performance issues](https://insights.project-a.com/manage-dependency-hell-supply-chain-attacks-and-performance-issues-a01a3e8e5231) was originally published in [Project A Insights](https://insights.project-a.com) on Medium.