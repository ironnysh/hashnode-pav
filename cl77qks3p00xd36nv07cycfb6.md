# GitHub Copilot will (not) take your job

How much would you pay to access public codebases from your IDE instead of spending hours sifting through Stack Overflow? What about the productivity boost you gain by never having to type the same code repeatedly? Would [you spend $0.27 a day](https://dev.to/seancassiere/continue-using-github-copilot-1hnp) to make your coding experience a little easier?

With Copilot — the latest addition to its arsenal of developer tools — GitHub hopes to [persuade numerous](https://news.ycombinator.com/item?id=31826890) developers and companies that its IDE extension can do all that and more for just $10/month or $100/year.

![A human’s hand reaching out to a robot with a screenshot of code in the background and flying GitHub Copilot logos hovering in between](https://cdn.hashnode.com/res/hashnode/image/upload/v1661352209189/KbyDKR94z.jpeg)<small>_Let me Copilot that for you (Background by Fahrul Razi @Unsplash | Hands by Tara Winstead @Pexels)_</small>

[Emerging](https://github.blog/2022-06-21-github-copilot-is-generally-available-to-all-developers/) from a 12-month closed beta, Copilot is powered by OpenAI’s [Codex](https://openai.com/blog/openai-codex/), a descendent of the company’s GPT-3 (Generative Pretrained Transformer). It leverages ML (machine learning) to suggest inline code snippets, rendering natural language into code.

Copilot works in **Visual Studio Code** , **Visual Studio** , **JetBrains IDEs** , and **Neovim** and supports over a dozen programming, markup, and templating languages, including **CSS, Go, HTML, JSON, JavaScript, Liquid, Markdown, Nunjucks, PHP, Perl, Python, Ruby, Shell, Swift, TypeScript** , and  **YAML**.

The AI determines developers’ intent based on context — comments, functions, and variable names — attempting to generate relevant snippets. Developers can cycle through up to ten suggestions, accept one, then alter the auto-generated code. Copilot learns from you, gradually adapting to corrections and edits to match your style and patterns.

### A cute sidekick

OpenAI touts its model as a valuable sidekick: “writing code can be thought of as (1) breaking a problem down into simpler problems, and (2) mapping those simple problems to existing code (libraries, APIs, or functions). The latter activity is probably the least fun part of programming (and the highest barrier to entry), and it’s where OpenAI Codex excels most”.

[More than 1.2 million people participated](https://github.blog/2022-06-21-github-copilot-is-generally-available-to-all-developers) in Copilot’s year-long technical preview, trying to determine if it’s truly a game-changer that redefines the industry or just a glorified autocomplete add-on.

> NYU’s study assessed the security of Copilot’s code and found it produced numerous bugs and security vulnerabilities

Dozens of developers, researchers, data scientists, and legal experts have been engaging in lengthy discussions about the future implications and potential (mi)use cases of GitHub’s “coding companion”, speculating whether it’s “[a blessing or a curse?](https://www.fast.ai/2021/07/19/copilot/)” But after using it for a few weeks in several web development projects, “cute” is the adjective that best encapsulates our impressions of this coding buddy.

While it liberated us from excessive typing, Copilot required thoughtful house-training before it could follow instructions. And like other cute things, it sometimes rambles with silly suggestions and endless repetitive loops.

One thing that stood out immediately was outdated JavaScript syntax; Copilot occasionally proposes ECMAScript 6 recommendations, like the spread operator or array destructuring, but rarely offers for...of loops, arrow functions, or template literals, and adapts to const/let only after you explicitly demand it. More than once, it recommended XMLHttpRequest instead of the newer, improved Fetch API and had similar oversights with CSS.

It was genuinely helpful in wrangling something using regular expressions:
```javascript
// write a regular expression script that matches the following: ])}while(1);</x>{ and replace with {
 
let sentence = 'beep]}while(1);<x>boop';
function replace(sentence) {
   return sentence.replace(/\]\}while\(1\);<x>/g, ', ');
}
 
console.log(replace(sentence)); // beep, boop
```

And even helped write this article — cute, right?
```javascript
// Create an array of words: Python, JavaScript, TypeScript, Ruby, Go, Perl, PHP, Swift, HTML, CSS, Shell, Liquid, Nunjucks, JSON, YAML, Markdown
// Create a function that takes the array of words and returns it in ascending order
// Call the function
// Output the result

let languages = ['Python', 'JavaScript', 'TypeScript', 'Ruby', 'Go', 'Perl', 'PHP', 'Swift', 'HTML', 'CSS', 'Shell', 'Liquid', 'Nunjucks', 'JSON', 'YAML', 'Markdown'];
function sortLanguages(languages) {
   return languages.sort();
}
console.log(sortLanguages(languages));
```

### Speed over quality

GitHub’s VP of product, Ryan J. Salva, [shared preliminary results of an unreleased study](https://techcrunch.com/2022/06/21/copilot-githubs-ai-powered-programming-assistant-is-now-generally-available/), revealing that developers who used Copilot to write an HTTP server were more likely to complete their task and did so “in roughly half the time.”

But GitHub’s so-called “AI pair programmer” scores lower in quality. An IEEE (Institute of Electrical and Electronics Engineers) paper examining whether [Copilot can substitute human pair-programming](https://ieeexplore.ieee.org/abstract/document/9793778) found that “although Copilot increases productivity [as measured by lines of code](https://insights.project-a.com/should-you-try-to-measure-developer-productivity-81733f2a8624) added, the quality of code produced is inferior”.

In our unscientific experiments, Copilot aced both [CodeAcademy’s](https://www.codecademy.com/resources/blog/20-code-challenges)and [Edabit’s](https://edabit.com/challenges) code challenges (we sampled the beginner, intermediate, and advanced categories). We don’t want to upset anyone, but the AI actually did better than two of our top engineers who participated in a noble experiment to test [Ballmer Peak](https://www.dictionary.com/e/pop-culture/ballmer-peak/#:~:text=Ballmer%20Peak%20is%20the%20name,between%200.129%25%20and%200.138%25).

> While it liberated us from excessive typing, Copilot required thoughtful house-training before it could follow instructions

If we had to bet, we’d gamble that Copilot can have at least two meaningful contributions:

1. Convince tech leads to [reconsider the practice](https://www.observationalhazard.com/2022/07/introductory-programming-assessment.html) of stressful coding challenges during job interviews.
2. Increase the demand for thoroughly diligent QA people, affirming Dave Rupert’s summary of his experience on the [ShopTalk Show](https://shoptalkshow.com/523/#t=23:07) podcast: “ **_I went from writing code to reading code, and now I’m code-reviewing this robot_**.”

### Whose code is it anyway?

Testing Copilot’s abilities, [software engineer Cassidy Williams](https://gist.github.com/cassidoo/6101ef0657665683b787aab5ae9465f4) came up with dozen of code samples to throw at it. An Amusingly subversive prompt was to write “a function that returns the most corrupt corporation in the world” — Copilot’s return is Microsoft, GitHub’s parent company, and OpenAI’s principal investor holding the exclusive license for GPT-3.

Microsoft’s involvement antagonizes many people who feel that the company has already fooled them once. The core of the controversy is the source of Copilot’s intelligence: Open-source code — specifically, the portions of its 159GB training dataset that originated from public GitHub repositories licensed under[copyleft licenses(https://opensource.org/licenses).

In a [widely-cited paper](https://arxiv.org/pdf/2107.03374.pdf), OpenAI’s researchers confirmed that not all of Codex’s suggestions are unique, and there’s a “less than 0.1%” chance that Copilot will present snippets of other people’s code. As tiny as it is, this probability bodes legal and ethical problems for businesses that consider implementing Copilot and for maintainers of GPL-licensed software.

![A screenshot showing code snippets and suggestions made by GitHub Copilot](https://cdn-images-1.medium.com/max/1024/1*AjcmW0X4YbcPtlgVVcRdpQ.png)<small>_When prompted, Copilot suggests up to ten code snippets (screenshot)_</small>

Github [promised](https://github.blog/2021-06-30-github-copilot-research-recitation/) to solve this by adding a feature to notify users of verbatim code suggestions. In the meantime, it [instructs users how to](https://github.com/features/copilot#what-can-i-do-to-reduce-github-copilot-s-suggestion-of-code-that-matches-public-code) ensure no questionable snippets slip through and opt out of [sharing data](https://github.com/features/copilot#faq-privacy) with the tech triumvirate.

But the company’s approach (“[training ML systems on public data is fair use](https://news.ycombinator.com/item?id=27676266&p=2#27678354)”) sparked a heated debate among open-source advocates. The Free Software Foundation (FSF) — long advising the community to use “other code hosting sites” — published an insightful[collection of whitepapers submitted following its open call](https://www.fsf.org/news/publication-of-the-fsf-funded-white-papers-on-questions-around-copilot), where academics weigh in on the legal and ethical aspects of GitHub’s tool.

On the other end of the spectrum, researcher Felix Reda [warned against](https://felixreda.eu/2021/07/github-copilot-is-not-infringing-your-copyright/) playing into the hands of corporations that benefit from stricter copyright laws: “the copyleft scene is essentially demanding an extension of copyright to actions that have for good reason not been covered by copyright. These extensions would have fatal consequences for the very open culture which copyleft licences seek to promote”.

### Bugs and security vulnerabilities

Copilot faces yet another challenge: Insecure and buggy code suggestions. NYU’s study [assessed the security of Copilot’s code](https://arxiv.org/pdf/2108.09293.pdf) and found it produced numerous bugs and security vulnerabilities:

> We used “Copilot to generate code in scenarios relevant to high-risk cybersecurity weaknesses […] producing 1,689 programs. Of these, we found approximately **40% to be vulnerable**.”

Commenting on the findings, Oege de Moor, VP of GitHub Next and one of Copilot’s developers,[assured Wired](https://www.wired.com/story/ai-write-code-like-humans-bugs/) that OpenAI uses manual and automated code reviews to reduce “the frequency of security vulnerabilities”.

Still, his colleagues at OpenAI [came to similar](https://arxiv.org/abs/2107.03374) conclusions, [acknowledging](https://venturebeat.com/2021/07/08/openai-warns-ai-behind-githubs-copilot-may-be-susceptible-to-bias/) that Copilot’s model requires human supervision: “Codex proposes syntactically incorrect or undefined code, invoking functions, variables, and attributes that are undefined or outside the scope. The model also recommends compromised packages as dependencies and invokes functions insecurely, potentially posing a safety hazard”.

![XKCD comics about the risks of public datasets: “When you train predictive models on input from your users, it can leak information in unexpected ways”](https://cdn-images-1.medium.com/max/546/0*NkzC0UF9yAAaK1xv)<small>_(Randall Munroe, CC BY-NC 2.5)_</small>

### The Invisible hand

The market’s preferred way of pushing companies to do better is through competition. However, Project A’s investment experts doubt that any small startup could take on deep-pocketed players with access to massive resources.

As mentioned above, Microsoft not only invested $1B in OpenAI but also licensed the exclusive rights to use GPT-3. With this resource out of reach, contenders need to train their own model — preferably after they secure financial backing: In 2019, researchers at the University of Massachusetts Amherst [estimated that](http://arxiv.org/abs/1906.02243) the cloud computing costs alone could reach $3.2M.

Ben Dickson recently [commented](https://bdtechtalks.com/2022/07/05/github-copilot-large-language-model-product-management/) that the release of Copilot

> **“is a reminder [that] the nature of LLMs (Large Language Model, R.S.) put large tech companies like Microsoft and Google at an unfair advantage to commercialize them–LLMs are not democratic”.**

Along with Amazon — the leading cloud infrastructure vendor — there are a few smaller players, including open-source projects, that hope to shift the power dynamics:

- [**Amazon CodeWhisperer**](https://aws.amazon.com/codewhisperer/) — a direct competitor to Copilot, CodeWhisperer is still in limited preview and only supports Java, JavaScript, and Python. The tool makes code suggestions based on comments and code patterns and has been trained “on billions of lines of code” from open-source repositories, internal Amazon repositories, API documentation, and forums. CodeWhisperer has three killer features: Tight integration into the AWS ecosystem, with specific code recommendations for its APIs; built-in security scans to detect vulnerabilities; and a component that indicates if a snippet is similar to the training data and references the original.
- [**Tabnine**](https://www.tabnine.com/) — a veteran in this relatively young field, Tabnine was first released in 2019. [in mid-June](https://www.tabnine.com/blog/announcing-tabnine-next-generation/), the company [announced its latest version](https://www.tabnine.com/blog/announcing-tabnine-next-generation/), which “uses a dozen code-native models […] trained from the ground-up on code”. Tabnine [strives to reassure](https://www.tabnine.com/code-privacy) both the business and open-source communities: It defused the GPL-landmine by skipping it entirely (its 400M-3B datasets trained only on MIT, Apache 2.0, BSD-2, and BSD-3 repositories) and pledges that “AI data are NEVER used to train any models other than [your own team models](https://twitter.com/drorwe/status/1539293063117516801)”.  
Tabnine supports 31 languages and 8 IDEs; free for Starter / $12 for Pro.

### Open-source projects

- [**BigScience**](https://bigscience.huggingface.co/blog/bloom) — the newest actor is a multi-national consortium of over[1,000 volunteer researchers](https://www.technologyreview.com/2022/07/12/1055817/inside-a-radical-new-project-to-democratize-ai/) backed by Hugging Face and the French government. The result is **_BLOOM_** (BigScience Large Open-science Open-access _Multilingual_ Language Model), an open-access LLM featuring 176B parameters (GPT-3 includes 175B).
- [**EleutherAI**](https://www.eleuther.ai/) — not a dedicated coding engine, EleutherAI’s open-source language models include 95GB of data sourced from GitHub. The “collective of researchers working to open source AI research” is involved in several projects, including the Pile — an 825GB training dataset.
- [**GPT-Code-Clippy (GPT-CC)**](https://github.com/CodedotAl/gpt-code-clippy/wiki) ** ** — this “community effort to create an open-source version of GitHub Copilot” launched in June 2021. It’s unclear if the project is still maintained, but there are publically available resources and demos to explore (including a[VSCode Insiders extension](https://github.com/WASANSPAPY/code-clippy-vscode)).

```javascript
// GitHub Copilot:

// Function to render products and prices in HTML divs

function renderProducts(products) {
   var html = '';
   for (var i = 0; i < products.length; i++) {
       html += '<div>' + products[i].name + ': $' + products[i].price + '</div>';
   }
   return html;
}

// Amazon CodeWhisper (*React-based example from https://aws.amazon.com/codewhisperer/):

// Function to render products and prices in HTML divs
function renderProducts(products, prices) {
   const productElements = products.map((product, index) => {
       return (
           <div key={index}>
               {product} - ${prices[index]}
           </div >
       );
   });
   return productElements;
}

```

***

#### Did you enjoy this story?
* Check out more stories on our [Tech Insights blog](https://insights.project-a.com/tech/home).

***

**[Originally published](https://insights.project-a.com/github-copilot-will-not-take-your-job-4454079cfda9) on Project A's Tech Insights Medium blog**
