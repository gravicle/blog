---
layout: post
title: OMG Markdown
date: 2014-09-04 07:42:53.000000000 -05:00
summary: Twitter erupted into its own little controversy. This time, @codinghorror got together with a bunch of smart fellas and tried to tame Markdown.
---
![](http://www.arcticencounters.net/perch/resources/writing-writing-31275199-1500-1004.jpg)
<p>Again, twitter erupted into its own little controversy. This time, <a href="https://twitter.com/codinghorror">@codinghorror</a> got together with a bunch of smart fellas and tried to <a href="http://standardmarkdown.com">tame Markdown</a>. This has sparked a lot of flame throwing with arguments ranging from hijacking what is, supposedly, John Gruber's project to claiming that someone on the internet is a dick (you guessed that one!).</p>

<blockquote class="twitter-tweet" lang="en"><p>Whether Gruber filed a trademark with the USPTO or not has no relevance on whether it’s a dick move to commandeer the name.</p>&mdash; Marco Arment (@marcoarment) <a href="https://twitter.com/marcoarment/status/507547724968128512">September 4, 2014</a></blockquote>

<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<p>I sympathize that Markdown is something Gruber conceived and it has been a hell of a contribution to the community. I cannot think of writing today any other way. In fact, Markdown's percolation has been astounding. It has been adopted as the de-facto input format across Github, StackOverflow, etc. and has a wonderful app ecosystem around it. However, it is a mistake to think that this happened <em>because</em> MD is so loosely defined.</p>

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/Gernot">@Gernot</a> And Markdown and RSS are both incredibly successful and popular.</p>&mdash; John Gruber (@gruber) <a href="https://twitter.com/gruber/status/507559105977147392">September 4, 2014</a></blockquote>

<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<p>I believe, MD has proliferated this far, not <em>because</em> it is an ambiguous, open to interpretation spec but <em>in-spite</em> of that. Just look at RSS or CSV. Every RSS-reader developer has some very quality things (NOT) to say about the standard. It's a loose cannon and a pain in the butt to deal with. CSV? The simple, nice "standard"? Just <a href="http://tburette.github.io/blog/2014/05/25/so-you-want-to-write-your-own-CSV-code/">try writing a parser for it</a>!</p>

<blockquote>
  <p>Writing CSV code that works with files out there in the real world is a difficult task. The rabbit hole goes deep. Ruby CSV library is 2321 lines.</p>
</blockquote>

<p>Markdown is getting there.</p>

<p>There are a lot of MD flavors. This is good. Most of these flavors implement core features differently. This is bad. As Markdown attains more and more popularity, the situation is just going to get worse. Remember the days when IE could not be bothered to care about standards compliant CSS implementations? This makes it hard for developers of services to roll out a simple MD parser to suit their needs. Instead, they need to go hunting for edge cases and account for all the different ways people can write the syntax. Makes it even more difficult to write apps which talk to each other. So, I do not concur with the argument that Markdown can succeed thru neglect. Proof? What people actually write in apps is some strict superset of MD which is defined by the developer. MD, as is used in practice, is not loose, not unsupervised. Problem is, there are too many cooks!</p>

<p>What I like about this effort to cast MD into a standard is that it will remove ambiguity from core features. This does not, in any way, strip anyone's ability to extend MD. Implement the standard core and then expand on it to better suit your and your users' needs. Most of the time, you won't need to.</p>

<p>Back to the issue of name!</p>

<blockquote class="twitter-tweet" lang="en"><p>If you didn’t like how I ran Overcast and started your own “Standard Overcast” project, you’d be hearing from my trademark lawyer.</p>&mdash; Marco Arment (@marcoarment) <a href="https://twitter.com/marcoarment/status/507531412594233344">September 4, 2014</a></blockquote>

<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<p>This is not a cogent argument. Overcast, for one, is not open source. It does not lend itself to forking. Markdown, on the other hand, is. However, <em>Standard Markdown</em> does violate <a href="http://daringfireball.net/projects/markdown/license">MD's BSD license</a>:</p>

<blockquote>
  <p>Neither the name “Markdown” nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.</p>
</blockquote>

<p>So does <a href="http://fletcherpenney.net/multimarkdown/">MultiMarkdown</a>. So does <a href="https://help.github.com/articles/github-flavored-markdown">Github Flavored Markdown</a>.
These are the two most popular implementations of MD and they use the word "Markdown" without reservation. Why the backlash now? Because, as opposed to those two, this one supposedly takes control away from John Gruber.</p>

<blockquote class="twitter-tweet" lang="en"><p>If you hate that so much that you need to make it a “standard” that YOU control, call it something new that doesn’t include “Markdown”.</p>&mdash; Marco Arment (@marcoarment) <a href="https://twitter.com/marcoarment/status/507528536291561472">September 4, 2014</a></blockquote>

<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

<p>Control that he never exercised. "Markdown" has not changed in the slightest since Dec 2004. Any other spec out there that is as widely used and as stagnant? Do we have the audacity to claim that v1.0.1 was perfect in every way imaginable? Then why do we have so many extensions, forks, and flavors<sup id="fnref-789:fn-1"><a href="#fn-789:fn-1" rel="footnote">1</a></sup>?</p>

<p><a href="http://daringfireball.net/projects/markdown/">John Gruber</a>:</p>

<blockquote>
  <p>I’ve set up a public mailing list for discussion about Markdown. Any topic related to Markdown — both its formatting syntax and its software — is fair game for discussion. Anyone who is interested is welcome to join.</p>
  
  <p>It’s my hope that the mailing list will lead to good ideas for future improvements to Markdown.</p>
</blockquote>

<p>On the other end, on the <a href="http://5by5.tv/systematic/50">Systematic episode from June 25th 2013</a>, at 37:40 mark, Gruber attests:</p>

<blockquote>
  <p>I used to participate on that mailing list, but I don't anymore. Cuz I kinda feel like it's (MD is) is effectively done.</p>
</blockquote>

<p>You should listen to it from that point on. Doesn't take a lot to realize that MD needs some sort of stewardship and Gruber, respectfully, doesn't feel the need to. However, I do not condone violating his license and if name is the point of contention, change away. Call it whatever. At this point, it's becoming pedantic.</p>

<p>However, objections to the idea of standardization are ill-informed and superstitious. It's a failure to understand what made MD a success. It's the fear that Gruber alludes to in that Systematic episode at around 38:00:</p>

<blockquote>
  <p>What's his name, Jeff Atwood, coding horror guy, every two years writes down something about how terrible I am at leading Markdown. [...]
  In the mean time, Markdown pages on Daring Fireball get twice the page views they ever got before. And there are more and more systems everyday that come out with Markdown. <strong>And part of that is because actually I don't screw it up</strong>.
  (emphasis mine)</p>
</blockquote>

<p>Fear of screwing up something that you do not know the cause of success of is not a healthy way to go about doing anything!</p>

<div class="footnotes">
<hr />
<ol>

<li id="fn-789:fn-1">
<p>Again, I am not against extensions. They serve a purpose. They make MD versatile enough for widespread use. But the existence of one particular <em>flavor</em>, MultiMarkdown, MMD, and its popularity speaks to the need for an actively revised spec that conforms to how people are using MD.&#160;<a href="#fnref-789:fn-1" rev="footnote">&#8617;</a></p>
</li>

</ol>
</div>
