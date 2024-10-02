# Largest-palindrome-product
Problem Statement
A palindromic number reads the same forwards and backwards. The smallest 6-digit palindrome made from the product of two 3-digit numbers is 101101.

Your task is to find the largest palindrome made from the product of two 3-digit numbers that is less than a given number 
𝑁
N.

Input Format
The first line contains 
𝑇
T, the number of test cases.
The next 
𝑇
T lines each contain an integer 
𝑁
N, representing the upper limit for the palindrome product in that test case.
Constraints
1
≤
𝑇
≤
100
1≤T≤100
101101
≤
𝑁
≤
1
0
6
101101≤N≤10 
6
 
Output Format
For each test case, print the largest palindrome made from the product of two 3-digit numbers that is less than 
𝑁
N.
SOLUTION:
#include <map>
#include <set>
#include <list>
#include <cmath>
#include <ctime>
#include <deque>
#include <queue>
#include <stack>
#include <string>
#include <bitset>
#include <cstdio>
#include <limits>
#include <vector>
#include <climits>
#include <cstring>
#include <cstdlib>
#include <fstream>
#include <numeric>
#include <sstream>
#include <iostream>
#include <algorithm>
#include <unordered_map>

using namespace std;


vector<int> GeneratePalindromes()
{
    set<int> palSet;
    int num = 101101, next;
    
    while(num <= 999999)
    {      
        for(int i=101; i<=999; i++)
        {
            if(num % i == 0 && to_string(num/i).length()==3) palSet.insert(num);
        }     
        string L = to_string(num).substr(0, 3), R;
        next = stoi(L) + 1;
        L = to_string(next);
        R = L;
        reverse(R.begin(), R.end());              
        num = stoi(L+R); 
    }
    vector<int> ret;
    copy(palSet.begin(), palSet.end(), back_inserter(ret));
    return ret;
}


int main()
{
    int t;
    cin >> t;
    
    vector<int> validPalindromes = GeneratePalindromes();
        
    while(t--)
    {        
        int n;
        cin>>n;
        
        auto it = find_if(validPalindromes.begin(), validPalindromes.end(), [=](int i) { return (i>=n); });
        cout<<*(--it)<<endl;
    }
    return 0;
}
