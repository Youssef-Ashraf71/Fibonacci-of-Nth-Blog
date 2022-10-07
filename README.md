
<!--
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8784836&assignment_repo_type=AssignmentRepo)  -->

# Fibonacci of Nth-Blog

## Contributors <a name = "Contributors"></a>

<table>
  <tr>
    <td align="center">
    <a href="https://github.com/Youssef-Ashraf71" target="_black">
    <img src="https://avatars.githubusercontent.com/u/83988379?v=4" width="150px;" alt="Youssef Ashraf"/>
    <br />
    <sub><b>Youssef Ashraf</b></sub></a>
      <p>Section 2 - Bench Number: Null</p>
    </td>
  </tr>
 </table>
 <h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://twitter.com/yoyobunt" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" alt="yoyobunt" height="30" width="40" /></a>
<a href="https://linkedin.com/in/yousssef-ashraf-a76633238" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="yousssef-ashraf-a76633238" height="30" width="40" /></a>
<a href="https://fb.com/100004525787159" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/facebook.svg" alt="100004525787159" height="30" width="40" /></a>
<a href="https://instagram.com/youssef_ashraf71" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="youssef_ashraf71" height="30" width="40" /></a>
<a href="https://www.hackerrank.com/youssef_aziz02" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/hackerrank.svg" alt="youssef_aziz02" height="30" width="40" /></a>
<a href="https://codeforces.com/profile/yoyobunt" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/codeforces.svg" alt="yoyobunt" height="30" width="40" /></a>
<a href="https://www.leetcode.com/yoyobunt" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/leet-code.svg" alt="yoyobunt" height="30" width="40" /></a>
</p>

# Content

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
 * O[1] (constant).
 
 
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


# 4-Using Matrix Exponentiation
## Theory 
* Matrix Exponentiation is a useful tool in solving not just the questions related to Fibonacci numbers but other linear recurrence equations too.

``` 
  The general recurrence relation for a series in which a term depends on the previous 2 terms is:
  f(n) = af(n-1) + bf(n-2)
  ( For Fibonacci, a=1 and b=1 )

The matrix form of this equation is:

| f(n) | = | p q | X | f(n-1) |

| f(n-1) | | r s | | f(n-2) |

Therefore, we get=
f(n) = p * f(n-1) + q * f(n-2)  and  f(n-1) = r * f(n-1) + s * f(n-2)
For each recurrence relation, the values of p,q,r and s will be different.
but in my code i used '
 new_a = 0 * a + 1 * b; &   new_b = 1 * a + 1 * b; 
To easily handle the special case n=0.
```

<p align="center" width="100%">
    <img width="70%" src="https://user-images.githubusercontent.com/83988379/194101016-9e11f9ea-d21b-42f4-9203-730380bdd625.png">
</p>

## Time Complexity: 
 * O[log(n)] as we are using fastpower Divide and Conquer Technique
 
## Space Complexity 
* O[1] 


## Code in C++
prefered constrains `0≤n≤91` or `0≤n≤10e18` by taking mod of 1e9+7.


###  Matrix Expoentiation Approach
```
#define ll long long
struct Matrix {
    ll a[2][2] = { {0,0},{0,0} };
    Matrix operator *(const Matrix& anatany) {
        Matrix Fib;
       for(int i=0;i<2;i++) {
           for (int j=0;j<2; j++) {
               for (int k=0;k<2; k++) {
                   Fib.a[i][k] = (Fib.a[i][k] + (ll) a[i][j] * anatany.a[j][k]) ;
               }
           }
       }
        return Fib;
    }
};
Matrix expoentiate(Matrix a, ll k) {
    Matrix Fib;
   for(int i=0;i<2;i++)  Fib.a[i][i] = 1;  
    while(k>0) {
        if(k&1) {
            Fib = Fib * a;
        }
        a=a*a;
        k/=2;
    }
    return Fib;
}
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    Matrix input;
    // rule >> [(0,1), (1,1)] n times
    input.a[0][0] = 0;
    input.a[0][1] = 1;
    input.a[1][0] = 1;
    input.a[1][1] = 1;
    Matrix answer = expoentiate(input,n);
    cout << answer.a[1][0] << endl;
}
```

# 5-Using Binet’s formula
## Theory 
* In this method, we directly implement the formula for the nth term in the Fibonacci series. 
* `Fn = {[(√5 + 1)/2] ^ n} / √5 `

## Time Complexity: 
 * O[Log N]
 
## Space Complexity 
* O[1] 


## Code in C++
prefered constrains `0≤n≤70`


### Binet’s formula Approach
```
ll fib(ll n) {
    double phi = (1 + sqrt(5)) / 2;
    return round(pow(phi,(double)n) / sqrt(5));
}
void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    cout<<fib(n)<<endl;
}
```

# 6-Using DP On Matrix Exponentiation
## Theory 
* one more interesting recurrence formula that can be used to find n’th Fibonacci Number.
* How this formula is derived?

![quicklatex com-eee4fa0c08f84de02fd9767ad0206d6c_l3](https://user-images.githubusercontent.com/83988379/194590164-7dc3ff2d-b4c5-468f-947f-94a80b3e28f8.svg)
```
Taking determinant on both sides, we get 

(-1)n = Fn+1Fn-1 - Fn2 
 
Moreover, since AnAm = An+m for any square matrix A, 
the following identities can be derived (they are obtained 
from two different coefficients of the matrix product)

FmFn + Fm-1Fn-1 = Fm+n-1         -------------------------->(1)

By putting n = n+1 in equation(1),
FmFn+1 + Fm-1Fn = Fm+n             ------------------------>(2)

Putting m = n in equation(1).
F2n-1 = Fn2 + Fn-12
Putting m = n in equation(2)

F2n = (Fn-1 + Fn+1)Fn = (2Fn-1 + Fn)Fn 
( By putting Fn+1 = Fn + Fn-1 )
To get the formula to be proved, we simply need to do the following 
If n is even(n&1->true), we can put k = n/2 
If n is odd(n&1->false), we can put k = (n+1)/2

```

## Time Complexity: 
 * O[Log N]
 
## Space Complexity 
* O[N] 


## Code in C++
prefered constrains `0≤n≤92`

```
vector<ll>dp((int)1e3,0);
ll fib(ll n)
{
    if (!n) return dp[n]=n;
    if (n == 1 || n == 2)  return dp[n]=1;
    if (dp[n])  return dp[n];
    ll po = (n & 1)? (n+1)/2 : n/2;
  return  dp[n] = (n & 1)? (fib(po)*fib(po) + fib(po-1)*fib(po-1)): (2*fib(po-1) + fib(po))*fib(po);
}

void solve()
{
    ll n,i=0,j=0,cnt=0;
    cin>>n;
    cout<<fib(n)<<endl;
}
```

# Comparison 

| Method                      | Time Complexity | Space Complexity |
|-----------------------------|-----------------|------------------|
|Recursion                    | O(2^N)          | O(N)             |
|Dynamic Programming          | O(N)            | O(N)             |
|Optimize on DP               | O(N)            | O(1)             |
|Matrix Exponentiation        | O(Log N)        | O(1)             |
|Binet’s formula              | O(Log N)        | O(1)             |
|DP On Matrix Exponentiation  | O(Log N)        | O(N)             |


# References
  * [Matrix Exponentiation 1](https://usaco.guide/plat/matrix-expo?lang=cpp)
  * [Matrix Exponentiation 2](https://www.youtube.com/watch?v=eMXNWcbw75E)
  * [Dynamic Programming](https://www.youtube.com/watch?v=YBSt1jYwVfU)
  * [Binet’s formula](https://www.sciencedirect.com/science/article/pii/S0195669807000595#:~:text=In%201843,%20Binet%20gave%20a,%5D,%20%5B28%5D)
  * [DP on Matrix Expo](https://www.geeksforgeeks.org/program-for-nth-fibonacci-number/)




