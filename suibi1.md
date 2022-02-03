$D:\\Desktop\\Code\\P1091.cpp$

# 乌龟棋
```cpp
#include<cstdio>
#include<iostream>
#include<algorithm>
using namespace std;
int N,M,a[10002],dp[41][41][41][41],b,c[5];
int main(){
	cin>>N>>M;
	for(int i=1;i<=N;i++){
		cin>>a[i];
	}
	for(int j=1;j<=M;j++){
		cin>>b;
		c[b]++;
	}
	dp[0][0][0][0]=a[1];
	for(int i=0;i<=c[1];i++){
		for(int j=0;j<=c[2];j++){
			for(int k=0;k<=c[3];k++){
				for(int l=0;l<=c[4];l++){
					int t=i+j+j+k+k+k+l+l+l+l+1;
					if(i>=1)dp[i][j][k][l]=max(dp[i][j][k][l],dp[i-1][j][k][l]+a[t]);
					if(j>=1)dp[i][j][k][l]=max(dp[i][j][k][l],dp[i][j-1][k][l]+a[t]);
					if(k>=1)dp[i][j][k][l]=max(dp[i][j][k][l],dp[i][j][k-1][l]+a[t]);
					if(l>=1)dp[i][j][k][l]=max(dp[i][j][k][l],dp[i][j][k][l-1]+a[t]);
				}
			}
		}
	}
	cout<<dp[c[1]][c[2]][c[3]][c[4]];
	return 0;
}
```
