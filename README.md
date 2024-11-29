# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

T(n) { 1 for n <= 1
       3T(n/3) + n<sup>5 for n > 1
       3 recursive calls within the function, each called with n/3
       triple nested loop, first loops from 0 to n<sup>2, second from 0 to n, third from 0 to n<sup>2, with a constant time calculation done inside. Thus giving us n^5 time.
       3(3T(n/3/3) + (n/3)^5) + n^5
       9T(n/9) + n^5/3^5 + n^5
       3^iT(n/3^i) + n^5/3^5i + ... + n^5
       find base case/termination condition in terms of i
       n/3^i = 1, i = log3(n)
       3^log3(n)T(n/3^log3(n)) + ... + n^5
       n * 1 + ... + n^5
       lower order terms ignored
       final answer O(n^5)
       
