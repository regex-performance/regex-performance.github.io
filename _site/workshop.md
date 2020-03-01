## Part 1: Warm-up

### 1. Repetition

Match HTML tags.

1. Add text inside/after the tag, see if step count changes; see debugger
2. Add another tag, see the result
3. Two solutions: limit repetition using lazy quantifier `.*?`, or limit scope `[^>]`
4. Try both, add text inside/after the tag, see step count changes

[Regex101](https://regex101.com/r/exsSjf/2)


### 2. Alternative

Optimize regex that finds certain CSS classes related to product: `product-size, product-column, product-info`
and product ids that has digits 1,2,3. [Regex101](https://regex101.com/r/WhQqEA/3/)


## Part 2: Understanding Catastrophe

### 1. Arithmetic operations.

You have a regex matching simple arithmetic operations. Allowed: two numbers
separated with plus or minus sign, ending with equals sign, e.g. `12+34=` or `32121-23=`

1. Enhance regex to allow 3 numbers and 2 signs (e.g. `12+322-1=` ).
1. Enhance regex to allow any lenght of the operation (e.g. `12+322-1+223-2323+...=`).
1. Remove equals sign from the test string, check steps in debugger.

[Regex101](https://regex101.com/r/qPsP27/3/)

When you're done, go to [demo page](https://regex-performance.github.io/vue-en.html)
and see impact of hastily written regex on user experience. To see timing stats, open browser console. Optimize the regex (you can start in Regex101 and apply it to the demo page).

### 2. Wrong way to parse CSV

Optimize regex matching `Tea` column in CSV text: [Regex101](https://regex101.com/r/CAo4Xx/1/)

## Part 3: Into the Wild
1. Analyse regex that stopped Cloudflare servers. Optimize it to remove catastrophic backtracking. [Regex101](https://regex101.com/r/fD4yMi/1/)
2. Analyse regex found by Sam Saffron at code written by a Discourse client. It replaces space before certain characters by HTML thin space (French typography). See how it performs on unexpected input. Optimize it. [Regex101](https://regex101.com/r/MDgdC6/1/)
3. Analyze regex used in a Microsoft project to match Windows username. Find an input causing catastrophic bactracking. Optimize it. [Regex101](https://regex101.com/r/8gaUFh/1/)
