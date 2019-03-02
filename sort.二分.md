# sort 二分

题见<https://blog.csdn.net/qq_34202873/article/details/79835482>

暴力循环
```

#include <bits/stdc++.h>
#include<iostream>
using namespace std;
const int maxn = 100010;
int a[maxn];
int b[maxn];
int c[maxn];

int main()
{
	int n;
	cin>>n;
	 for (int i=1;i<=n;i++)
	 {
	 	cin>>a[i];
	 }
	  for (int i=1;i<=n;i++)
	 {
	 	cin>>b[i];
	 }
	  for (int i=1;i<=n;i++)
	 {
	 	cin>>c[i];
	 }
	 sort(a+1,a+1+n);
	 sort(b+1,b+1+n);
	 sort(c+1,c+1+n);
	 int count =0;
	 for (int i=1;i<=n;i++)
	 {
	 	for (int j=1;j<=n;j++)
	 	{
	 		if (a[i]<b[j]){
	 			for (int k=1;k<=n;k++)
	 		   {
	 		      if (b[j]<c[k])
	 		      {
	 		      	count++;
				   }
				   else
				   {
				   	break;
				   }
			    }
			 }
			 else{
			 	break;
			 }
	 	
		 }
	 }
	 printf("%d",count);
	 
	
} 

```
二分

- 将三个数组排序 ，以b数组位准则，找到 小于 b[]的个数与 小于 c[] 的个数，乘积 累加

```

#include<bits/stdc++.h>
using namespace std;
const int MAXN = 100005;
int a[MAXN],b[MAXN],c[MAXN];
int n,sum;

int main()
{
  cin>>n;
  for(int i=0;i<n;i++)scanf("%d",&a[i]);
  for(int i=0;i<n;i++)scanf("%d",&b[i]);
  for(int i=0;i<n;i++)scanf("%d",&c[i]);
  sort(a,a+n);
  sort(b,b+n);
  sort(c,c+n);
  sum = 0;
  for(int i=0;i<n;i++){
    int x = (lower_bound(a,a+n,b[i]) - a);//返回第一个 大于位置
    int y = (n - (upper_bound(c,c+n,b[i]) - c));//返回第一个小于的位置
    sum += x*y;
  }
  cout<<sum;
  return 0;
}
--------------------- 
转载
https://blog.csdn.net/qq_34202873/article/details/79835482 

```