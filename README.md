实验五 数组 
一、实验目的 
1、掌握一维数组和二维数组的定义、赋值和输入输出的方法。 
2、掌握字符数组和字符串函数的使用。 
3、掌握与数组有关的算法（特别是排序算法）。 
 
二、实验准备 
1、复习数组的基本知识。 
2、复习字符串数组的特点和常用的字符串处理函数。 
 
三、实验内容 
编写下列问题的源程序并上机调试运行。 
1、用选择法对10个整数排序(10个整数用scanf函数输入)。 
#include<stdio.h> 
int main()
{
    int i;
    int n = 10;
    int shuzi[n];
    int zj;
    for(i = 0;i < n;i++){
        scanf("%d",&shuzi[i]);
    }
    for(i = 0;i < n - 1;i++){
        for(int j = 0;j < n - i - 1;j++){
            if(shuzi[j] > shuzi[j + 1]){
                zj = shuzi[j];
                shuzi[j] = shuzi[j + 1];
                shuzi[j + 1] = zj;
            }
        }
    }
    for(i = 0;i < n;i++){
        printf("%d ",shuzi[i]);
    }
    printf("\n");
    return 0;
}
![image](https://github.com/user-attachments/assets/51fd7db6-e2a5-419f-8a6a-cdf738c096db)

2、有15个数存放在一个数组中，输入一个数，要求用折半查找法找出该数是数组中第几个
元素的值。如果该数不在数组中，则输出“无此数”。15个数用赋初值的方法在程序中给出。
要找的数用scanf函数输入。 
#include <stdio.h>
int main()
{
    int i;
    int num;
    int a[15];
    for(i = 0;i < 15;i++){
        scanf("%d",&a[i]);
    }
    scanf("%d",&num);
    for(i = 0;i < 15;i++){
        if(a[i] == num){
            printf("%d\n",i);
        }
    }
    return 0;
}
![image](https://github.com/user-attachments/assets/1e667ad4-2d41-4853-bf93-f12b7a15f65c)

3、将两个字符串连接起来，不要用strcat函数。 
#include <stdio.h>
int main()
{
    char c1[100],c2[100];
    gets(c1);
    gets(c2);
    printf("%s%s",c1,c2);
    return 0;
}
![image](https://github.com/user-attachments/assets/f9bb313c-1d8e-4166-9b1e-a293da2e6569)

4、找出一个二维数组的“鞍点”，即该位置上的元素在该行上最大，在该列上最小。也可能
没有鞍点。此二维数组可以设定如下，其中，数组元素的值用赋初值方法在程序中指定。 
9 80 205 40 
90 -60 96 1 
210 -3 101 89
#include <stdio.h>

void SaddlePoints(int n, int m, int arr[n][m]) {
    int hasSaddlePoint = 0; 

    for (int i = 0; i < n; i++) {
        int maxValRow = arr[i][0];  
        int colIndex = 0; 

     
        for (int j = 1; j < m; j++) {
            if (arr[i][j] > maxValRow) {
                maxValRow = arr[i][j];
                colIndex = j;
            }
        }
        int isSaddlePoint = 1;  
        for (int k = 0; k < n; k++) {
            if (k!= i && arr[k][colIndex] < maxValRow) {
                isSaddlePoint = 0;
                break;
            }
        }
        if (isSaddlePoint) {
            printf("%d %d %d\n", maxValRow, i, colIndex);
            hasSaddlePoint = 1;
        }
    }
    if (hasSaddlePoint == 0) {
        printf("NO\n");
    }
}

int main() {
    int n, m;
    scanf("%d %d", &n, &m);
    int arr[50][50];  
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            scanf("%d", &arr[i][j]);
        }
    }

    SaddlePoints(n, m, arr);

    return 0;
}
