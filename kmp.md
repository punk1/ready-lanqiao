# kmp 算法
  
  
```
#include<iostream>
#include <string>
#include <cstdio>
#include<queue>
#include <stack>
#include <algorithm>
#include <cstring>
#include <cmath>
using namespace std;
typedef long long ll;
int t;
int n, m;
const int maxn = 1e6 + 10;
const int maxm = 1e4 + 10;
int a[maxn];
int b[maxm];
int nexta[maxm];
void getnext(int q[])
{
	nexta[0] = -1;
	int k = -1;
	int i = 0;
	while (i<m)
	{
		if (k == -1 || q[i] == q[k])
		{
			i++;
			k++;
			nexta[i] = k;
		}
		else
			k = nexta[k];
	}
}
int kmp()
{
	int i = 0, j = 0;
	while (i < n)
	{
		if (a[i] == b[j] || j == -1)
		{
			i++;
			j++;
		}
		else
			j = nexta[j];
		if (j == m)
			return i - j + 1;
  
	}
	return -1;
}
int main()
{
	int ans;
	scanf("%d", &t);
	while (t--)
	{
		scanf("%d%d", &n, &m);
		for (int i = 0; i < n; i++)
		{
			scanf("%d", &a[i]);
		}
		for (int i =0; i < m; i++)
		{
			scanf("%d", &b[i]);
		}
		getnext(b);
		ans=kmp();
		if (n < m)
			printf("-1\n");
		else
		printf("%d\n", ans);
	}
	return 0;
}
  
  
```
  