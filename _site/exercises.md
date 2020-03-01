# Regex Performance Exercises

## Test Apps
* [input validation](https://regex-performance.github.io/input-en.html)
* [pattern search](https://regex-performance.github.io/vue-en.html)

## Exercise 1
<!--![](img/qr/spa/greedy.jpeg) -->
[https://link.do/spa-greedy](https://link.do/spa-greedy)

Match HTML tags.

1. Add text inside/after the tag, see if step count changes; see debugger
2. Add another tag, see the result
3. Two solutions: limit repetition using lazy quantifier `.*?`, or limit scope `[^>]`
4. Try both, add text inside/after the tag, see step count changes

Hints:
* `X*` greedy quantifier
* `X*?` lazy quantifier
* `[XYZ]` character set, `[^XYZ]` negated character set

## Exercise 2
[https://link.do/spa-possessive](https://link.do/spa-possessive)

Match numbers with units ending with semicolon: `123cm; 32kg; 1m3;`


1.  Try to add digits to the number
2.  Remove semicolon - see steps and backtracking in debugger
3.  Replace greedy quantifier with the possessive one `++`, see steps in debugger

Hints:
* `\d` digit
* `\w` word character (digit, letter, underscore)
* `X++` possessive quantifier


## Exercise 3
Optimize those two expressions:
 1. Match `Tea` column in CSV text: [https://link.do/spa-csv](https://link.do/spa-csv)
 2. (\*) Find some CSS classes related to product: `product-size, product-column, product-info`
and product ids that has digits 1,2,3. [https://link.do/spa-css](https://link.do/spa-css)

Hints:
* `^` beginning of the line
* `(?:...)` non-capturing group
* `X{6}` repeat 6 times

## Exercise 5 (\*)

[https://link.do/spa-operations](https://link.do/spa-operations)

Arithmetic operations.

You have a regex matching simple arithmetic operations. Allowed: two numbers
separated with plus or minus sign, ending with equals sign, e.g. `12+34=` or `32121-23=`

1. Enhance regex to allow 3 numbers and 2 signs (e.g. `12+322-1=` ).
1. Enhance regex to allow any lenght of the operation (e.g. `12+322-1+223-2323+...=`).
1. Remove equals sign from the test string, check steps in debugger.

## References
* Mastering Regular Expressions, 3rd Edition, Jefferey Friedl, 2009
* [Regex101 - online regex tester and debugger](https://regex101.com/)
* [Test app - original](https://github.com/kszubrycht/regex-with-vuejs) thanks to [Kamil Szubrycht](https://github.com/kszubrycht)
* [OWASP on ReDoS](https://www.owasp.org/index.php/Regular_expression_Denial_of_Service_-_ReDoS)
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
