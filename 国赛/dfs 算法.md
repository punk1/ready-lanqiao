# dfs 算法

- https://blog.csdn.net/hzj1998/article/details/80492044  第二题

  1. dfs  起始位置
  2. dfs  函数：中止条件，每个点往下递归的可能性 （此题注意 当左边为0时 ，右边 有两种情况）
  3. 回溯，进行其他可能的递归

  ```
  #include <iostream>
  #include <algorithm> 
  #include <cstring>
  using namespace std;
  int x[31];
  int ans = 0;
  void dfs (int index)
  {
  	if (index == 30)
  	{
  		ans++;
  		return ;
  	}
  	else
  	{
  	// 递归的 可能有两种情况
  		if (index==0|| x[index-1]==0)
  		{
  			for (int i=0;i<=1;i++) // 递归的可能 有两种情况
  			{
  			x[index]=i;
  			dfs(index+1);
  			x[index]=0; // 回溯
  			}
  		
  		}
  		else
  		{
  			dfs(index+1);
  		}
  	}
  }
  int main()
  {
  	memset (x,0,sizeof(x));
  	dfs(0);
  	cout << ans << endl;
  	return 0;
  }
  ```

  