# Regex Performance Exercises

## Test Apps
* [input validation](https://regex-performance.github.io/input-en.html)
* [pattern search](https://regex-performance.github.io/vue-en.html)

## Exercise 1
<!--![](img/qr/spa/greedy.jpeg) -->
[https://link.do/spa-greedy](https://link.do/spa-greedy)

Match HTML tags. 

1. Add text inside/after the tag, see if step count changes; see debugger </li>
2. Add another tag, see the result</li>
3. Two solutions: limit repetition `.*?`, limit scope `[^>]` </li>
4. Try both, add text inside/after the tag, see step count changes </li>

Hints:
* `X*` greedy quantifier
* `X*?` lazy quantifier
* `[XYZ]` character set, `[^XYZ]` negated character set

## Exercise 2
[https://link.do/spa-possessive](https://link.do/spa-possessive)

Match numbers with units ending with semicolon: `123cm; 32kg; 1m3;` 


1.  Try to add digits to the number  </li>
2.  Remove semicolon - see steps and backtracking in debugger</li>
3.  Replace greedy quantifier with the possessive one `++`, see steps in debugger  </li>

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
* http://www.rexegg.com
* https://www.regular-expressions.info
* https://regex101.com/
* [Russ Cox](https://swtch.com/~rsc/regexp/regexp1.html) and next parts (1-4)
* [test app - original](https://github.com/kszubrycht/regex-with-vuejs) thanks to [Kamil Szubrycht](https://github.com/kszubrycht)
* [OWASP ReDoS](https://www.owasp.org/index.php/Regular_expression_Denial_of_Service_-_ReDoS)
* [Loggly: 5 techniquess](https://www.loggly.com/blog/five-invaluable-techniques-to-improve-regex-performance/)
* [Loggly: regexes bad better...](https://www.loggly.com/blog/regexes-the-bad-better-best/)
* [Katafrakt: Regular expression how do they work?](http://katafrakt.me/2016/07/06/regular-expressions/)
* [The true power of regular expressions](http://nikic.github.io/2012/06/15/The-true-power-of-regular-expressions.html)
* [FlashText algorithm vs regular epxressions for keyword matching](https://www.analyticsvidhya.com/blog/2017/11/flashtext-a-library-faster-than-regular-expressions/)
