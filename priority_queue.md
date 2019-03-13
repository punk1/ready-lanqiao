# 优先队列
  
题意：
第1500 个丑数值是多少
  
- 它的模板声明带有三个参数，priority_queue<Type, Container, Functional>
Type 为数据类型， Container 为保存数据的容器，Functional 为元素比较方式。
Container 必须是用数组实现的容器，比如 vector, deque 但不能用 list.
STL里面默认用的是 vector. 比较方式默认用 operator< , 所以如果你把后面俩个
参数缺省的话，优先队列就是大顶堆，队头元素最大。
greater 小顶堆
  
```
#include <cstdio>
#include <cstdlib>
#include <cmath>
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
#include <algorithm>
#include<queue>
#include <map>
#include <set>
#include <stack>
using namespace std;
typedef long long   ll;
int a[3] = { 2,3,5 };
set<ll >s;
priority_queue<ll, vector<ll >, greater <ll> >pq;
int main()
{
	s.insert(1);
	pq.push(1);
	for (int i = 1;; i++)
	{
		ll x = pq.top();
		pq.pop();
		if (i == 1500)
		{
			printf("The 1500'th ugly number is %lld.\n", x);
			break;
		}
		for (int j = 0; j < 3; j++)
		{
			ll x2 = x * a[j];
			if (!s.count(x2))
			{
				s.insert(x2);
				pq.push(x2);
  
			}
		}
	}
	return 0;
}
```
  