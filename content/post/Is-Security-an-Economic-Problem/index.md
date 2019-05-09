---
title: 'Is Security an Economic Problem?'
subtitle: ''
summary: ''
authors:
- admin
tags: [security, secure, programming, Economic, problem, devices, developers, development]
categories: []
date: "2017-04-13T00:00:00Z"
lastmod: "2017-04-13T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  caption: ''
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

---

Is Security an Economic Problem? This post attempts to address an issue that is controversial in nature, but will (in my opinion) nevertheless become important, and will inevitably have to be addressed. Do not read this post as a call for change, but as a call for thought and open discussion. This may be a unique opportunity to discuss a topic before it becomes a problem in practice and the emotions set in.

Humans, perhaps because we evolved to thrive in an landscape of large objects with semi-predictable behavior where details do not matter, seem to have a hard time being precise because we don’t always care about the fine details every time (Even if the details matter). But however, computers don’t have this issue. They run code to a t, without hesitating on every step. This is good in most cases, but not in situations where emotions and double checking are required, or at least preferred. E.G. Saving a life based on statistics vs cognitional thinking about it. This is a different issue altogether, but this gives context about the problem at hand here in this post.

Computer code can, in principle, be perfect or at least be secure. This is because the code includes every instruction needed to run. There exist correct programs with perfect security properties. It’s hard, however, for us to find them because the difference between a correct program and an incorrect one can be as small as one character. Writing ‘=’ instead of ‘==’ can be the difference between a program that works flawlessly and a program that ends up causing significant financial loss.

It is possible for humans to write correctly secure programs, but doing so is very expensive. Each line of code needs hours of review, and adequate test suites may need to be larger than than the software they are testing. One view of security research is as the systematic study of how to make writing correct programs cheaper and easier. One dream is to create a development platform in which it’s impossible or difficult to create programs with vulnerabilities. We have taken significant steps towards this dream, as evidenced by technologies like DEP and ASLR which transform some insecure programs into secure ones, but the goal is still miles away.

An alternate approach is to keep our current systems where it is easy to make mistakes but train the people using them not to make mistakes. This is possible in principle, but expensive. It has been my experience that people only learn when they are actually interested in the subject for themselves. I find it difficult to believe that any software developer who “just wants to get the job done” will ever be able to write secure or correct code. Passion and patience is necessary. So we’re left with a dilemma. If we want secure code, we have to fork over hefty sums of money to pay the rare people who truly care, or wait for a technological silver bullet. It’s not exactly a dichotomy; there’s a trade-off. Developers need to be skilled enough to not make mistakes within the framework they’re given. As the technological solutions get better, we can be satisfied with less and less competent developers. But technological solutions to high-level design flaws seem unlikely, so some degree of skill will always be required.

Secure software has to compete with insecure software. As long as we are willing to pay for an insecure program that is cheaper than its secure equivalent, insecurity will continue to dominate the market. It’s hard to tell the difference between a secure program and an insecure program, though. It costs a lot to find vulnerabilities, which is good because it means we are harder to attack, but it’s also a bad thing because it stops us from knowing whether the software we use is secure or not. Because it’s so easy to mask incorrect software behind a beautiful reliable-seeming interface, insecure software will always provide fierce competition. A company willing to gamble on security can undercut the security-focused competition and win, even if everyone was willing to pay more for secure software, simply because it’s hard to tell the difference between the two.

Given this state of affairs, how will we ever realistically attain widespread security? I can see only three ways: (1) We develop a reliable and cheap indicator of software correctness, so the market can ask for the level of correctness it needs, (2) A technological solution comes along that makes secure code just as cheap as writing insecure code, or (3) Instead of buying software from a third party, develop the software internally, controlling the entire process, hiring passionate security engineers, and so on (beware “Not Invented Here” syndrome).

We might also attain widespread security by taking some combination of these options. Option (2) is unrealistic. As mentioned before, skill will always be necessary, and as long as there is no reliable and cheap indicator of software quality, it will be possible to undercut the competition by refusing to pay for that skill and instead focusing on showing off a false sense of security through a robust-looking interface. Option (3) is possible, and we do it (think: NASA’s lunar lander code), but it is not sustainable. Code re-use between distrusting organizations isn’t possible. It’s impossible, while there is no reliable and cheap quality indicator, for an organization to prove to anyone on the outside that they really did invest in making their product secure.

That leaves option (1) as our only way forward. The way forward is to make a reliable and cheap indicator of code quality, so that the market can pay for the security level that it needs. A perfect technological indicator is believed to be impossible. Indeed, high-level social issues escape formal analysis, and even the computational problem of deciding whether a piece of code is secure is intractable (NP-hard or even undecidable). All other indicators, with two known exceptions (more on these later), are heuristic in nature. An experienced engineer can look over a code base to get a sense for how “clean” it is, and the author’s reputation is some indication. We can not rely on these indicators either because they are unsustainable (only trusting software that was written by someone with a good reputation is a form of Not Invented Here syndrome), or because they are unreliable (it’s possible to spend money to make code look “clean” without actually making it secure).

The two exceptions alluded to above are: (1) Proofs of correctness, and (2) Software testing. If a software firm published efficiently-verifiable proofs of correctness with all of their software, we could cheaply know that it is secure. Proving the correctness of software is an actively evolving area of research, which is advancing slowly but surely. With any luck, it may turn out to be a viable solution. But there is no doubt that providing proofs will be expensive. The other exception, software testing, is somewhere in between a formal measure like a proof and a heuristic reputation-based indicator. If software comes with an extensive test suite, wherein every line of code is tested in many different ways, and all conceivable edge cases are tried, we can be confident that the program is correct. Developing good tests is cheaper than writing a complete proof of correctness. Being more formal in nature, these indicators are hard to fake. It’s not possible to provide a proof unless what you’re proving is true. It’s not possible to provide a passing test suite unless the functionality the test suite is looking for actually exists. These are good options, and hopefully the industry will come to recognize them as important, not just on the developer side, but also when making the decision of what software to buy. Failing formal proofs and tests, we have to consider “social” constructs which can serve as a quality indicator.

It’s hard or impossible to find software today that comes with a warranty, and so there is no recourse against the software company if something goes wrong. In special cases there could be. For example, if an error in Boeing’s code resulted in a crash killing hundreds of people, there may be legal consequences. But in general, there aren’t, and I don’t think there should be. Software is incompatible with legal recourse because most bugs show up at the meeting of two abstraction layers and so it’s hard to decide who to blame. If Company A uses Company B’s library in their product, and a bug in Company B’s library causes Company A’s software to kill someone, then whose fault is it, Company A’s or Company B’s? Surely not Company B’s since it is impractical for developers of a library to agree to and review every use of their library. Also not Company A’s, because the source code to Company B’s library may not have been available to them, and they would have no means to check if it is secure.

– This post was coauthored by [Taylor Hornby](https://defuse.ca/) and myself.