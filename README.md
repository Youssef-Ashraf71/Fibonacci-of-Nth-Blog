# Fibonacci of Nth-Blog



<p align="center" width="100%">
    <img width="70%" height=400px src="https://user-images.githubusercontent.com/83988379/193649172-c308df87-5a69-40ca-81bf-70bcf62981b6.jpg">
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
* By optimization and taking the size of the function call stack into consideration we will find it O[N].

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

# 2-Using Dynamic Programming(memoization conecpt)
## Theory 
* from the definition `Fn = Fn-1 + Fn-2` we can easily calculate the nth fibonacci number.
### Top Down
* Base Case  ?? > first 2 Elements in the series [0,1].
* Transition ?? > fib(n)=fib(n-1)+fib(n-2) so our answer for the sub-problem is fib(n-1)+fib(n-2).
* `BUT` We optimize on the recursion by using DP(Using memoization to avoid repeating subproblems) so we can avoid the repeated work done in #1 by storing the Fibonacci numbers calculated so far. 
* so we compute the result and store it in the array, associating the result with the input that generated it. The next time the same subproblem needs to be solved, the corresponding result will already be in the array so you can access it linearly.

### Bottom Up
* start with the first 2 known numbers in the sequence and then buid your answer till reach fib(N)
 using the transition formula `Fn = Fn-1 + Fn-2`.

## Time Complexity: 
 * O[N] but you can easily linearly access any fib number smaller than `N` in O[1] if you have solved for `N`.

## Space Complexity 
* O[N].


<p align="center" width="100%">
    <img width="50%" src="https://user-images.githubusercontent.com/83988379/193692450-bfbb9b20-95fa-4c04-87f0-2b10b693e9f2.jpg">
</p>



## Code in C++
prefered constrains `0≤n≤91` for good time compilation.
### Recursive Approach(Top down)
```
#define ll long long
#include<vector>
vector<ll>dp(100,0);
ll rec(ll n){
    // base case
    if(!n) return dp[0]=1;
    if(n==1) return dp[1]=1;
    
    // dp memoisation
    if(dp[n]) return dp[n];
    // transition
    return dp[n]=rec(n-1)+rec(n-2);
}
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    if(n==1) cout<<n<<endl;
    else cout<<rec(n);
}
```

### Iterative Approach(Bottom Up)
```
#define ll long long
vector<ll>dp(10000,0);
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    // series indexed from F0,F1,F2,....
    dp[0]=0; dp[1]=1;
    for(i=2;i<=n;i++){
        dp[i]=dp[i-1]+dp[i-2];
    }
    cout<<dp[n]<<endl;
}
```


# 3-Optimize on Dynamic Programming in #2
## Theory 
* We can optimize the space used in method 2 by storing the previous two numbers only because that is all we need to get the next Fibonacci number in series till reaching fib(N). 
## Time Complexity: 
 * O[N]
## Space Complexity 
* O[1](constant time).
## Code in C++
prefered constrains `0≤n≤91` for good time compilation.
### Iterative Approach(Bottom Up)
```
#define ll long long
ll first=0,second=1;
void init(){
    first=0; second=1;
}
void fib(ll n){
   for(ll i=2;i<=n;i++){
        ll next=first+second;
        first=second; second=next;
   }
}
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    fib(n); cout<<second<<endl; init();
}
```

