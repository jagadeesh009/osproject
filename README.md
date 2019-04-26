#include<stdio.h>
int main()
{
int i, limit, sum = 0, n,x, count = 0, timequantum,j;
int wait = 0, tat = 0,pos,z,p[10],prio[10], a_time[10],
b_time[10], temp[10],b;
	  printf("\t\t\t\t\t*****************************************\n");
	  printf("\t\t\t\t\t\t** Prepared by - JAGADEESH**\n");
	  printf("\t\t\t\t\t**Reg No. 11702509 Roll No. K17YP - B52 **\n");
	  printf("\t\t\t\t\t*****************************************\n");
printf("\nEnter Total Number of Processes:");
scanf("%d", &limit);
x = limit;
n=limit;
for(i = 0; i < limit; i++)
{
p[i]=i+1;
prio[i]=0;
printf("\nEnter sum Details of Process[%d]\n", i + 1);
printf("Arrival Time:\t");
scanf("%d", &a_time[i]);
printf("Burst Time:\t");
scanf("%d", &b_time[i]);
temp[i] = b_time[i];
}
printf("\nEnter the Time Quantum:");
scanf("%d", &timequantum);
printf("\nProcess ID\tBurst Time\t Turnaround Time\t Waiting Time\n");
for(sum = 0, i = 0; x != 0;)
{
for(z=0;z<limit;z++)
{
int temp1;
pos=z;
for(j=z+1;j<limit;j++)
{
if(prio[j]<prio[pos])
pos=j;
}
temp1=prio[z];
prio[z]=prio[pos];
prio[pos]=temp1;
temp1=b_time[z];
b_time[z]=b_time[pos];
b_time[pos]=temp1;
temp1=a_time[z];
a_time[z]=a_time[pos];
a_time[pos]=temp1;
temp1=p[z];
p[z]=p[pos];
p[pos]=temp1;
temp1=temp[z];
temp[z]=temp[pos];
temp[pos]=temp1;
}
{
}
if(temp[i] <= timequantum && temp[i] > 0)
{
sum = sum + temp[i];
temp[i] = 0;
count = 1;
}
else if(temp[i] > 0)
{
temp[i] = temp[i] - timequantum;
sum = sum + timequantum;
}
for(b=0;b<limit;b++)
{
if(b==i)
prio[b]+=1;
else
prio[b]+=2;
}
if(temp[i] == 0 && count == 1)
{
x--;
printf("\nProcess[%d]\t\t%d\t\t %d\t\t %d", p[i],b_time[i], sum-a_time[i], sum-a_time[i]-b_time[i]);
wait = wait+sum-a_time[i]-b_time[i];
tat = tat+sum-a_time[i];
count = 0;
}
if(i == limit - 1)
{
i = 0;
}
else if(a_time[i + 1] <= sum)
{
i++;
}
else
{
i = 0;
}
}
printf("\n\n\tAverage Waiting Time = %f" , (float)wait/n);
printf("\n\tAverage Turn Around Time = %f" , (float)tat/n);
return 0;
}
