# dfs 算法
- 地图类
   
   - 1:初始化 方向
   ```
   int dx[]={-1,0,1,0};
   int dy[]={0,1,0,-1};
   ``` 
   2:设置标记数组 ,并初始化
   ```
   int vis [7][7];//标记是否访问过 
   	for (int i=0;i<7;i++)
	{
		for (int j=0;j<7;j++)
		{
			vis[i][j]=0;
		}
	}
   ```
   3.从起点开始dfs遍历
   ```
   vis[3][3]=1;
   dfs(3,3);
   ```
   4。dfs遍历
 ```
   void dfs(int x,int y)
{
	if (x==0||y==0||x==6||y==6)//边界条件 结束 
	{
		ans++;
		return;
	}
	//四个方向走 
	for (int k=0;k<4;k++)
	{
		int xx = x+ dx[k];
		int yy= y+ dy[k];
		//满足条件的进入dfs下个位置 
		if (xx>=0&&6-xx>=0&&yy>=0&&6-yy>=0&&vis[xx][yy]==0&&xx<=6&&6-xx<=6&&yy<=6&&6-yy<=6&&vis[6-xx][6-yy]==0)
		{
			vis[xx][yy]=1;
			vis[6-xx][6-yy]=1;//标记访问过 
			dfs(xx,yy);
			vis[xx][yy]=0;//回溯 
			vis[6-xx][6-yy]=0;
		}
	}
}
 ```

 5:完整代码  题见<https://blog.csdn.net/y1196645376/article/details/69718192>第四题
```
#include <bits/stdc++.h>
#include<iostream>
int dx[]={-1,0,1,0};
int dy[]={0,1,0,-1};
int ans =0;
int vis [7][7];//标记是否访问过 
void dfs(int x,int y)
{
	if (x==0||y==0||x==6||y==6)//边界条件 结束 
	{
		ans++;
		return;
	}
	//四个方向走 
	for (int k=0;k<4;k++)
	{
		int xx = x+ dx[k];
		int yy= y+ dy[k];
		//满足条件的进入dfs下个位置 
		if (xx>=0&&6-xx>=0&&yy>=0&&6-yy>=0&&vis[xx][yy]==0&&xx<=6&&6-xx<=6&&yy<=6&&6-yy<=6&&vis[6-xx][6-yy]==0)
		{
			vis[xx][yy]=1;
			vis[6-xx][6-yy]=1;//标记访问过 
			dfs(xx,yy);
			vis[xx][yy]=0;//回溯 
			vis[6-xx][6-yy]=0;
		}
	}
}
int main()
{
	for (int i=0;i<7;i++)
	{
		for (int j=0;j<7;j++)
		{
			vis[i][j]=0;
		}
	}
	
	//从起点开始dfs 遍历 
	vis[3][3]=1;
	dfs(3,3);
	printf("%d ",ans/4);
}
 ```
   