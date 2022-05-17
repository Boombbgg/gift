#include<stdio.h>
#define N 3
typedef struct student 
{
	char country[20];
	float num;
}std;

void sr(std *,int );
void xie(std *,int );
void du(std *,int );
void sc(std *,int );

int main()
{
	std sx[N],sxt[N];
	sr(sx,N);
	xie(sx,N);
	du(sxt,N);
	sc(sxt,N);
	return 0;
}

void sr(std sx1[],int n)
{
	int i,j,t;
	for(i=0;i<n;i++)
	{
		printf("请输入第%d行信息：\n",i+1);
		printf("国家  金牌数：\n");
		scanf("%s%f",&sx1[i].country,&sx1[i].num);
	}

	for(i=1;i<n;i++)
	for(j=0;j<n-i;j++)
	if(sx1[j].num < sx1[j+1].num)
	{
		t=sx1[j].num;
		sx1[j].num=sx1[j+1].num;
		sx1[j+1].num=t;
	}
	
}

void xie(std sx2[],int n)
{
	FILE *fp;
	int i;
	if((fp=fopen("d:\\y\\lzy\\text.txt","wb"))==NULL)
	{
		printf("文件打开失败！！！\n");
		return ;
	}
	for(i=0;i<n;i++)
	{
		fwrite(&sx2[i],sizeof(std),1,fp);
	}
	rewind(fp);
	fclose(fp);
}

void du(std sx3[],int n)
{
	FILE *fp;
	int i;
	if((fp=fopen("d:\\y\\lzy\\text.txt","rb"))==NULL)
	{
		printf("文件打开失败！！！\n");
		return ;
	}
	for(i=0;i<n;i++)
	{
		fread(&sx3[i],sizeof(std),1,fp);
	}
	fclose(fp);
	return ;
}

void sc(std sx4[],int n)
{
	int i;
	for(i=0;i<n;i++)
		printf("%d\t%s\t%f\n",i+1,sx4[i].country,sx4[i].num);

}
