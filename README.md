#include<stdlib.h>
#include<stdio.h>
int main()
{
    int n,max,m;
    printf("请输入最大行数n(n<=15)");
    scanf("%d",&n);
    max=2*n-1;//算出矩阵的边长    
    int a[100][1000]={0};
    a[0][(max+1)/2-1]=1;
    a[1][(max+1)/2-2]=a[1][(max)/2+1]=1;
    int l;//l表示前面要留出几个空
    for(int i=2;i<n;i++){//i表示第几行
        m=2*(i+1)-1;
        l=(max-m)/2;
        a[i][l]=a[i][max-l-1]=1;
        for(int j=l+2;j<=max-l-3;j=j+2){
            a[i][j]=a[i-1][j+1]+a[i-1][j-1];
        }
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<max;j++){
            if(a[i][j]!=0){
                printf("%4d",a[i][j]);
            }else{
                printf("    ");
            }
        }
        printf("\n");
    }
    system("pause");
    return 0;
}
