# zuoye3
This is a test
#include<bits/stdc++.h>
using namespace std;
int num[10][10];
int w;
int min1=100;
int n;
struct book{
    int x;
    int y;
}p[100];
void search(int n1)
{
    if(p[n1].x==n-2&&p[n1].y==n-2)

    {
        if(min1>n1)
        min1=n1;
        return;
    }
    if(num[p[n1].y-1][p[n1].x]==0)
    {
        p[n1+1].x=p[n1].x;
		p[n1+1].y=p[n1].y-1;

        num[p[n1].y][p[n1].x]=1;
		search(n1+1);
		num[p[n1].y][p[n1].x]=0;
    }
    if(num[p[n1].y][p[n1].x+1]==0)
    {
        p[n1+1].x=p[n1].x+1;
		p[n1+1].y=p[n1].y;
		num[p[n1].y][p[n1].x]=1;
		search(n1+1);
		num[p[n1].y][p[n1].x]=0;
    }
    if(num[p[n1].y+1][p[n1].x]==0)
    {
        p[n1+1].x=p[n1].x;
		p[n1+1].y=p[n1].y+1;
		num[p[n1].y][p[n1].x]=1;
		search(n1+1);
		num[p[n1].y][p[n1].x]=0;
    }
    if(num[p[n1].y][p[n1].x-1]==0)
    {
        p[n1+1].x=p[n1].x-1;
		p[n1+1].y=p[n1].y;
		num[p[n1].y][p[n1].x]=1;
		search(n1+1);
		num[p[n1].y][p[n1].x]=0;
	}
}
int main()
{
	int i,j;
	cin>>n;
	for(i=0;i<n;i++)
	for(j=0;j<n;j++)
	cin>>num[i][j];
	p[0].x=1;
	p[0].y=1;		//这里为出发点，（n-2,n-2）为终点 										
	search(0);
	if(min1==100)	//如果min的值不改变，说明没有找到路径										
	cout<<"No solution"<<endl;
	else
	cout<<min1<<endl;
}
    
