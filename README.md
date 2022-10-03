# Fibonacci of Nth-Blog

<p align="center" width="100%">
    <img width="70%" height=200px src="https://user-images.githubusercontent.com/83988379/193649172-c308df87-5a69-40ca-81bf-70bcf62981b6.jpg">
</p>

# Definition 
* The Fibonacci numbers are the numbers in the following integer sequence.
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ……..

In mathematical terms, the sequence Fn of Fibonacci numbers is defined by the recurrence relation `Fn = Fn-1 + Fn-2`


# 1-Using Recursion 

## Time Complexity: 
  * Exponential :: T(2^N), as it forms a Tree where each call of the function calls 2 other times so let's imagine the first call as a Parent and the 2 other calls as a      child for the parent, you will find a Binary Tree formed.
 * Note: Binary tree is a tree where each parent has 2 childs so it's time complexity is 2^N 
<p align="center" width="100%">
    <img width="50%" src="https://user-images.githubusercontent.com/83988379/193652325-0b3a22c1-05cc-4dc2-a787-591c71a2e241.png">
</p>

## Space Complexity 
By optimization and taking the size of the function call stack into consideration we will find it O[N].

## Code in C++
prefered constrains `0≤n≤40` for good time compilation (1s) per test.
```
#define ll long long
ll fib(ll n){
    if(!n) return 0;
    if(n==1) return 1;
    return fib(n-1)+fib(n-2);
}
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    cout<<fib(n);
}
```
