
## Intro

Test those two simple pages that uses regex:

1. [Simple input, without JS (validation)](https://regex-performance.github.io/input-en.html)
1. [Editable regex (search)](https://regex-performance.github.io/vue-en.html)

## Part 1: Warm-up

### 1. Repetition

[Regex101](https://regex101.com/r/exsSjf/2)<br />
You need to match HTML tags. (In general case it's [a bad idea](https://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags/1732454#1732454) to use regex for HTML parsing, but it's a good learning example).

1. Add text inside/after the tag, see if step count changes; see debugger
2. Add another tag, see the result
3. There are two solutions: limit repetition using lazy quantifier `.*?`, or limit scope `[^>]`. Try both, add text inside/after the tag, see step count changes



### 2. Alternative
[Regex101](https://regex101.com/r/WhQqEA/3/)<br />
Optimize regex that finds certain CSS classes related to product: `product-size, product-column, product-info`
and product ids that has digits 1,2,3.


## Part 2: Understanding Catastrophe

### 0. Artificial example

[Regex101](https://regex101.com/r/MosMwT/1/) <br />
Watch the step count and the debugger while doing those changes:
1. Add more `a` at the beginning
2. Remove `b`

### 1. Arithmetic operations.

[Regex101](https://regex101.com/r/qPsP27/3/)<br />
You have a regex matching simple arithmetic operations. Allowed: two numbers
separated with plus or minus sign, ending with equals sign, e.g. `12+34=` or `32121-23=`

1. Enhance regex to allow 3 numbers and 2 signs (e.g. `12+322-1=` ).
1. Enhance regex to allow any lenght of the operation (e.g. `12+322-1+223-2323+...=`).
1. Remove equals sign from the test string, check steps in debugger.

When you're done, go to the [editable regex demo page](https://regex-performance.github.io/vue-en.html)
and see impact of hastily written regex on user experience. To see timing stats, open browser console. Optimize the regex (you can start in Regex101 and apply it to the demo page).

### 3. Wrong way to parse CSV

[Regex101](https://regex101.com/r/CAo4Xx/1/)<br />
You have a regex matching 6th column (`Tea`) in CSV file (again, there are better ways to parse CSV...). It's rather slow even for valid input. Optimize it.

## Part 3: Into the Wild


### 1. Cloudflare
[Regex101](https://regex101.com/r/fD4yMi/1/) <br />
Analyse regex that stopped Cloudflare servers. Optimize it to remove catastrophic backtracking.

### 2. Discourse customer
[Regex101](https://regex101.com/r/MDgdC6/1/) <br />
Analyse regex found by Sam Saffron at code written by a Discourse client. It replaces space before certain characters by HTML thin space (French typography). See how it performs on unexpected input. Optimize it.

### 3. Microsoft
[Regex101](https://regex101.com/r/8gaUFh/1/) <br />
Analyze regex used in a Microsoft project to match Windows username. Find an input causing catastrophic bactracking. Optimize it.

## Cheatsheet

### Operators:
* `X*` greedy quantifier (match as much as possible)
* `X*?` lazy quantifier (match as little as possible)
* `X*+`, `X++` possessive quantifiers (don't backtrack)
* `X{n}` repeat n times
* `[XYZ]` character set, `[^XYZ]` negated character set
* `\d` digit
* `\w` word character (digit, letter, underscore)
* `^` beginning of the line
* `(?:...)` non-capturing group

###  Good practices

* `.* => [^X]*`
* `.*? => [^X]*`

* `(pre-d1|pre-e2|...) => pre-(d1|e2|...)`
* `(,|;|\.) => [,.;]`

* `(A+|B?)+ => A+(BA+)*` (unrolling the loop)
* `(A+|B?)+ => (A+B)*A+` (unrolling the loop)
* `(A+|B?)+ => (A++|B?)+` (avoiding backtracking by using possessive quantifiers)

## References

* Mastering Regular Expressions, 3rd Edition, Jefferey Friedl, 2009
* [Regex101 - online regex tester and debugger](https://regex101.com/)
* [Test app - original](https://github.com/kszubrycht/regex-with-vuejs) thanks to [Kamil Szubrycht](https://github.com/kszubrycht)
* [OWASP on ReDoS](https://www.owasp.org/index.php/Regular_expression_Denial_of_Service_-_ReDoS)
* [Maciek Rząsa: Performance of Regular Expressions](https://medium.com/textmaster-engineering/performance-of-regular-expressions-81371f569698)
* [Katafrakt: Regular expression how do they work?](http://katafrakt.me/2016/07/06/regular-expressions/)
* [The true power of regular expressions](http://nikic.github.io/2012/06/15/The-true-power-of-regular-expressions.html)
* [FlashText algorithm vs regular epxressions for keyword matching](https://www.analyticsvidhya.com/blog/2017/11/flashtext-a-library-faster-than-regular-expressions/)
* [Sam Safron: Debugging 100% CPU usage in production Ruby on Rails systems](https://samsaffron.com/archive/2018/01/18/my-production-ruby-on-rails-cpu-is-at-100-now-what
)
* [Jeff Atwood: Regex performance](https://blog.codinghorror.com/regex-performance/)
* [Mimicking atomic groups in JS regex](http://blog.stevenlevithan.com/archives/mimic-atomic-groups)
* [RexEgg - Regex Tutorial](http://www.rexegg.com), especially:
  * [Explosive quantifiers](http://www.rexegg.com/regex-explosive-quantifiers.html)
  * [Mastering quantifiers](http://www.rexegg.com/regex-quantifiers.html)
* [regular-expressions.info](https://www.regular-expressions.info):
  * [Possesive quantifiers](https://www.regular-expressions.info/possessive.html)
  * [Catastrophic backtracking](https://www.regular-expressions.info/catastrophic.html)
  * [Regex engine internals](https://www.regular-expressions.info/engine.html)
* Russ Cox regex series:
  * [Regular Expression Matching Can Be Simple And Fast](https://swtch.com/~rsc/regexp/regexp1.html)
  * [Regular Expression Matching: the Virtual Machine Approach](https://swtch.com/~rsc/regexp/regexp2.html)
  * [Regular Expression Matching in the Wild](https://swtch.com/~rsc/regexp/regexp3.html)
  * [Regular Expression Matching with a Trigram Index](https://swtch.com/~rsc/regexp/regexp4.html)
* Loggly:
  * [Five invaluable techniques to improve regex performance](https://www.loggly.com/blog/five-invaluable-techniques-to-improve-regex-performance/)
  * [Regexes bad, better, best](https://www.loggly.com/blog/regexes-the-bad-better-best/)
* ReDoS cases:
  * [Sam Safron: Debugging 100% CPU usage in production Ruby on Rails systems](https://samsaffron.com/archive/2018/01/18/my-production-ruby-on-rails-cpu-is-at-100-now-what)
  * [CloudFlare postmortem (2019)](https://blog.cloudflare.com/details-of-the-cloudflare-outage-on-july-2-2019/)
  * [StackOverflow postmortem (2016)](https://stackstatus.net/post/147710624694/outage-postmortem-july-20-2016)
* ReDoS research (Virginia Tech):
  * [Blogpost](https://medium.com/bugbountywriteup/introduction-987fdc4c7b0)
  * [Paper](http://people.cs.vt.edu/~davisjam/downloads/publications/DavisCoghlanServantLee-EcosystemREDOS-ESECFSE18.pdf)
