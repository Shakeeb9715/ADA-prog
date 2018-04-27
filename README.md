# ADA-prog

adjecency matrix

#include<iostream>
using namespace std;

int main()
{
 int n;
 cout<<"Enter the value of n\n";
 cin>>n;
 char b[n];
 cout<<"Enter the node\n";
 for(int i=0;i<n;i++)
 cin>>b[i];
 int a[n][n];
 cout<<"Enter the values in the matrix\n";
 for(int i=0;i<n;i++)
 {
  for(int j=0;j<n;j++)
  {
   cin>>a[i][j];
   if(a[i][j]==0)
    cout<<"There is no connection between\t"<<b[i]<<"\tand\t"<<b[j]<<"\n";
   else
    cout<<"There is a connection between\t"<<b[i]<<"\tand\t"<<b[j]<<"\n";
  }
 }
return 0;
}

bfs

#include<iostream>
using namespace std;
int a[20][20], q[20], visited[20], n, i, j, f = 0, r = -1;

void bfs(int v)
{
 for(i = 1; i <= n; i++)
  if(a[v][i] && !visited[i])
   q[++r] = i;
  if(f <= r)
  {
   visited[q[f]] = 1;
    bfs(q[f++]);
  }
}

int main()
{
 int v;
 cout<<"\n Enter the number of vertices:";
 cin>>n;

 for(i=1; i <= n; i++)
 {
 q[i] = 0;
 visited[i] = 0;
 }

 cout<<"\n Enter graph data in matrix form:\n";
 for(i=1; i<=n; i++)
  {
 for(j=1;j<=n;j++)
 {
 cin>>a[i][j];

  }

 }

 cout<<"\n Enter the starting vertex:";
 cin>>v;
 bfs(v);
 cout<<"\n The node which are reachable are:\n";

 for(i=1; i <= n; i++) {
 if(visited[i])
 cout<<i<<"\t";
 else {
 cout<<"\n Bfs is not possible. Not all nodes are reachable";
 break;
}
}
return 0;
}


bubblesort


#include<iostream>
using namespace std;

int main()
{
 int a[]={10,9,8,7,6,5,4,3};
 int n=8;
 for(int i=0;i<n-1;i++)
 {
  for(int j=0;j<n-i-1;j++)
  if(a[j]>a[j+1])
   { int temp=a[j+1];
    a[j+1]=a[j];
    a[j]=temp;
   }
 }

 cout<<"The array is\n";
 for(int i=0;i<n;i++)
 cout<<a[i]<<"\t";
 return 0;
}




floyd


#include <iostream>
using namespace std;

void floyds(int b[][7])
{
    int i, j, k;
    for (k = 0; k < 7; k++)
    {
        for (i = 0; i < 7; i++)
        {
            for (j = 0; j < 7; j++)
            {
                if ((b[i][k] * b[k][j] != 0) && (i != j))
                {
                    if ((b[i][k] + b[k][j] < b[i][j]) || (b[i][j] == 0))
                    {
                        b[i][j] = b[i][k] + b[k][j];
                    }
                }
            }
        }
    }
    for (i = 0; i < 7; i++)
    {
        cout<<"\nMinimum Cost With Respect to Node:"<<i<<endl;
        for (j = 0; j < 7; j++)
        {
            cout<<b[i][j]<<"\t";
        }
    }
}
int main()
{
        int b[7][7];
        cout<<"ENTER VALUES OF ADJACENCY MATRIX\n";
        for (int i = 0; i < 7; i++)
        {
                cout<<"enter values for\n"<<(i+1)<<" row"<<endl;
                for (int j = 0; j < 7; j++)
                cin>>b[i][j];
        }
        floyds(b);
        return 0;
}



heap


#include<iostream>
using namespace std;

int main()
{
  int a[100],n,i,j,c,root,temp;
  cout<<"Enter the number of elements\n";
  cin>>n;
  for(int i=0;i<n;i++)
  cin>>a[i];
  for(int i=1;i<n;i++)
  {
   c=i;
   do
    {
     root=(c-1)/2;
     if(a[root]<a[i])
      {
       temp=a[root];
       a[root]=a[c];
       a[c]=temp;
      }
     c=root;
    }
    while(c!=0);
  }
 cout<<"Heap Array\n";
 for(int i=0;i<n;i++)
 {
  cout<<a[i];
  for(j=n-1;j>=0;j--)
  {
   temp=a[c];
   a[c]=a[j];
   a[j]=temp;
  root=0;

  do
    {
      c=root+1;
      if(a[c]<a[c+1]&&c<j-1)
      {
        temp=a[root];
        a[root]=a[c];
        a[c]=temp;
      }
    root=c;
    }
    while(c<j);
  }
 }
cout<<"The sorted array is\n";
for(i=0;i<n;i++)
 cout<<a[i]<<"\t";

return 0;
}
interpolation

#include<iostream>
using namespace std;
int  interp(int arr[],int n, int x)
{
 int l=0;
 int h=n-1;
 while(l<=h&&x>=arr[l]&&x<=arr[h])
 {
  int pos = l+(((double(h-l))/(arr[h]-arr[l]))*(x-arr[l]));
  if(arr[pos]==x)
   return pos;
  if(arr[pos]<x)
   l=pos+1;
  else
   h=pos-1;
 }
return -1;
}

int main()
{
 int arr[]={10,20,30,40,50,60,70,80,90,100};
 int x;
 cout<<"Enter the element to be searched\n";
 cin>>x;
 int index=interp(arr,10,x);
 if(index!=-1)
 cout<<"Element found at index "<<index;
 else
  cout<<"Element not found";
 return 0;
}



krukal


#include<iostream>
#include<stdlib.h>
using namespace std;
int cost[10][10], i, j, k, n, m, c, visit, visited[10], l, v, count, count1,
  vst, p;

main ()
{
  int dup1, dup2;
  cout << "enter no of vertices\n";
  cin >> n;
  cout << "enter no of edges\n";
  cin >> m;
  cout << "EDGE Cost\n";
  for (k = 1; k <= m; k++)
    {
      cin >> i >> j >> c;
      cost[i][j] = c;
      cost[j][i] = c;
    }
  for (i = 1; i <= n; i++)
    for (j = 1; j <= n; j++)
      if (cost[i][j] == 0)
        cost[i][j] = 31999;
  visit = 1;
  while (visit < n)
    {
      v = 31999;
      for (i = 1; i <= n; i++)
        for (j = 1; j <= n; j++)
          if (cost[i][j] != 31999 && cost[i][j] < v && cost[i][j] != -1)
            {
              int count = 0;
              for (p = 1; p <= n; p++)
                {
                  if (visited[p] == i || visited[p] == j)
                    count++;
                }
              if (count >= 2)
                {
                  for (p = 1; p <= n; p++)
                    if (cost[i][p] != 31999 && p != j)
                      dup1 = p;
                  for (p = 1; p <= n; p++)
                    if (cost[j][p] != 31999 && p != i)
                      dup2 = p;

                  if (cost[dup1][dup2] == -1)
                    continue;
                }
              l = i;
              k = j;
              v = cost[i][j];
            }
      cout << "edge from " << l << "-->" << k;
      cost[l][k] = -1;
      cost[k][l] = -1;
      visit++;
      int count = 0;
      count1 = 0;
      for (i = 1; i <= n; i++)
        {
     if (visited[i] == l)
            count++;
          if (visited[i] == k)
            count1++;
        }
      if (count == 0)
        visited[++vst] = l;
      if (count1 == 0)
        visited[++vst] = k;
    }
return 0;
}



linear


#include<iostream>
using namespace std;
int main()
{
 int a[]={3,8,1,6,2,10,12,20};
 int l,i,j=1;
 cout<<"Enter the element you want to search\n";
 cin>>l;
 for(i=0;i<8;i++)
 {
  if(a[i]==l)
  { cout<<"Element found\n";
   j=2;
   break;
  }
 }
 if(j==1)
 cout<<"Element not found\n";

return 0;
}

n-queens


#include<stdio.h>
#define N 4
void printSolution(int board[N][N])
{
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
            printf(" %d ", board[i][j]);
        printf("\n");
    }
}

bool isSafe(int board[N][N], int row, int col)
{
    int i, j;
    for (i = 0; i < col; i++)
        if (board[row][i])
            return false;

    for (i=row, j=col; i>=0 && j>=0; i--, j--)
        if (board[i][j])
            return false;

    for (i=row, j=col; j>=0 && i<N; i++, j--)
        if (board[i][j])
            return false;

    return true;
}

bool solveNQUtil(int board[N][N], int col)
{
    if (col >= N)
        return true;

    for (int i = 0; i < N; i++)
    {
        if ( isSafe(board, i, col) )
        {
            board[i][col] = 1;
            if ( solveNQUtil(board, col + 1) )
                return true;
            board[i][col] = 0; // BACKTRACK
        }
    }

    return false;
}
bool solveNQ()
{
    int board[N][N] = { {0, 0, 0, 0},
        {0, 0, 0, 0},
        {0, 0, 0, 0},
        {0, 0, 0, 0}
    };

    if ( solveNQUtil(board, 0) == false )
    {
      printf("Solution does not exist");
      return false;
    }
    printSolution(board);
    return true;
}

int main()
{
 solveNQ();
 return 0;
}



prims

#include<iostream>
#include<stdlib.h>
using namespace std;
int cost[10][10], i, j, k, n, stk[10], top, v, visit[10], visited[10], u;

int main ()
{
  int m, c;
  cout << "enter no of vertices";
  cin >> n;
  cout << "enter no of edges";
  cin >> m;
  cout << "\nEDGES Cost\n";
  for (k = 1; k <= m; k++)
    {
      cin >> i >> j >> c;
      cost[i][j] = c;
    }
  for (i = 1; i <= n; i++)
    for (j = 1; j <= n; j++)
      if (cost[i][j] == 0)
        cost[i][j] = 31999;

  cout << "ORDER OF VISITED VERTICES";
  k = 1;
  while (k < n)
    {
      m = 31999;
      if (k == 1)
        {
          for (i = 1; i <= n; i++)
            for (j = 1; j <= m; j++)
              if (cost[i][j] < m)
                {
                  m = cost[i][j];
                  u = i;
                }
        }
      else
        {
          for (j = n; j >= 1; j--)
            if (cost[v][j] < m && visited[j] != 1 && visit[j] != 1)
              {
                visit[j] = 1;
                stk[top] = j;
                top++;
                m = cost[v][j];
                u = j;
              }
        }
      cost[v][u] = 31999;
      v = u;
      cout << v << " ";
      k++;
      visit[v] = 0;
      visited[v] = 1;
    }
  return 0;
}



quick

#include<iostream>
using namespace std;

void swap (int *a, int *b)
{
  int c = *a;
  *a = *b;
  *b = c;
}

int part (int low, int high, int arr[])
{
  int pi = arr[high];
  int i = low - 1, j = low;
  for (; j < high; j++)
    {
      if (arr[j] <= pi)
        {
          i++;
          swap (arr[i],arr[j]);

        }
cout<<pi<<"\t"<<arr[high]<<"\n";
}
  swap (&arr[i + 1], &arr[high]);
 for(int k=0;k<=high;k++)
 cout<<arr[k]<<"\t";

  return i + 1;

}

void quick (int low, int high, int arr[])
{
  if (low < high)
    {
      int pi = part (low, high, arr);
      quick (low, pi - 1, arr);
      quick (pi, high, arr);
    }
}

int main ()
{
  int arr[] = { 3, 2, 45, 6, 3, 56, 7, 8, 24 };
  quick (0, 8, arr);
  for (int i = 0; i <= 8; i++)
    {
      cout << arr[i] << "\t";
    }

  return 0;
}


research

#include<iostream>
using namespace std;
int search(int a[],int s,int l,int e)
{
 if(s>=l)
 return 0;
 else if(e==a[s])
  return 1;
 search(a,++s,l,e);
}

int main()
{
 int a[]={3,8,1,6,2,10,12,20};
 int l;
 cout<<"Enter the element you want to search\n";
 cin>>l;
 nclude<iostream>
using namespace std;
int search(int a[],int s,int l,int e)
{
 if(s>=l)
 return 0;
 else if(e==a[s])
  return 1;
 search(a,++s,l,e);
}

int main()
{
 int a[]={3,8,1,6,2,10,12,20};
 int l;
 cout<<"Enter the element you want to search\n";
 cin>>l;
 if( search(a,0,8,l))
  cout<<"Element found\n";
 else
  cout<<"Not found\n";
 return 0;
}
if( search(a,0,8,l))
  cout<<"Element found\n";
 else
  cout<<"Not found\n";
 return 0;
}



topol

#include<iostream>
using namespace std;

int main()
{
 int i,j,n,k,arr[100][100],ind[100],flg[100],count=0;
 cout<<"Enter the number of vertices\n";
 cin>>n;
 cout<<"Enter the adjacency matrix\n";
 for(i=0;i<n;i++)
  for(j=0;j<n;j++)
   cin>>arr[i][j];
 cout<<"\n";
 for(i=0;i<n;i++)
 {
  ind[i]=0;
  flg[i]=0;
 }

 for( i=0;i<n;i++)
  for( j=0;j<n;j++)
   ind[i]+=arr[j][i];
cout<<"The Topological order is\n";
while(count<n)
{
 for( k=0;k<n;k++)
 {
  if(ind[k]==0&&flg[k]==0)
   { cout<<k+1<<"\t";
     flg[k]=1;
   }
  for( i=0;i<n;i++)
   if(arr[i][k]==1)
    ind[k]--;
 }
count++;
 }

return 0;

}



bresearch

#include<iostream>
using namespace std;
int search(int a[],int s,int l,int e)
{
 if(s>=l)
 return 0;
 int m=(s+l)/2;
 if(e<a[m])
  search(a,s,m-1,e);
 else if(e==a[m])
  return 1;
 else
  search(a,m+1,l,e);
}

int main()
{
 int a[]={1,4,5,8,9,10,34,45};
 int l;
 cout<<"Enter the element you want to search\n";
 cin>>l;
 if( search(a,0,8,l))
  cout<<"Element found\n";
 else
  cout<<"Not found\n";
 return 0;
}


GCD

#include<iostream>
using namespace std;

int main()
{
 int a,b,c;
 cout<<"Ente the numbers";
 cin>>a>>b;
 c=b%a;
 while(c!=0)
 {
  b=a;
  a=c;
 c=b%a;
 }
cout<<"The GCD is\n";
cout<<a;
return 0;
}


knapsack


#include<stdio.h>
int maxim (int a, int b)
{
  if (a > b)
    return a;
  else
    return b;
}

int main ()
{
  int v[20][20], n, w[20], p[20], max, i, j;
  printf ("enter the number of elements:\n");
  scanf ("%d", &n);
  printf ("enter the weights\n");
  for (i = 1; i <=n; i++)
    scanf ("%d", &w[i]);
  printf ("enter profits:\n");
  for (i = 1; i <= n; i++)
    scanf ("%d", &p[i]);
  printf ("enter the maximum weight\n");
  scanf ("%d", &max);
  for (i = 0; i <= n; i++)
    v[i][0] = 0;
  for (j = 0; j <= max; j++)
    v[0][j] = 0;
  for (i = 1; i <= n; i++)
    {
      for (j = 1; j <= max; j++)
        {
          if (w[i] > j)
            v[i][j] = v[i - 1][j];
          else
            v[i][j] = maxim (v[i - 1][j], v[i - 1][j - w[i]] + p[i]);
        }
    }
  printf ("table\n");
  for (i = 0; i <= n; i++)
  { for (j = 0; j <= max; j++)
      printf ("\t %d", v[i][j]);
  printf ("\n");}

printf("maxprofit is %d ", v[n][max]);
printf("subset of items considered to per max profit is \n");
j = max;
for (i = n; i >= 1; i--)
  {
    if (v[i][j] != v[i - 1][j])
      {
        printf ("%d", i);
        j = j - w[i];
      }
  }
return 0;
}



merge

#include<iostream>
using namespace std;

void merge(int arr[],int l,int m,int r)
{
 int i=l;
 int j=m+1;
 int k=0;
 int a[8];
 while(i<m&&j<r)
 {
  if(arr[i]<arr[j])
  {
   a[k]=arr[i];
   k++;
   i++;
  }
  else
  {
   a[k]=arr[j];
   k++;
   i++;
  }
}
 while(i<m)
 {
  a[k++]=arr[i++];
 }
  while(j<r)
 {
  a[k++]=arr[j++];
 }

 for(int i=l;i<r;i++)
  arr[i]=a[i-l];
 //
// return a;
}


void mergesort(int arr[],int l,int r)
{

if(l<r)
 {
  int m = (l+r-1)/2;
  mergesort(arr,l,m);
  mergesort(arr,m+1,r);
  merge(arr,l,m,r);
 }
}

void printarr(int arr[],int l,int r)
{
 for(int i=l;i<r;i++)
  cout<<arr[i]<<"\t";
}

int main()
{
 int arr[]={1,23,4,56,7,8,17,10};
 int n=8;
// printarr(arr,0,7);
 mergesort(arr,0,8);
 printarr(arr,0,8);
 return 0;
}



quick

#include<iostream>
using namespace std;

void swap (int *a, int *b)
{
  int c = *a;
  *a = *b;
  *b = c;
}

int part (int low, int high, int arr[])
{
  int pi = arr[high];
  int i = low - 1, j = low;
  for (; j < high; j++)
    {
      if (arr[j] <= pi)
        {
          i++;
          swap (arr[i],arr[j]);

        }
cout<<pi<<"\t"<<arr[high]<<"\n";
}
  swap (&arr[i + 1], &arr[high]);
 for(int k=0;k<=high;k++)
 cout<<arr[k]<<"\t";

  return i + 1;

}

void quick (int low, int high, int arr[])
{
  if (low < high)
    {
      int pi = part (low, high, arr);
      quick (low, pi - 1, arr);
      quick (pi, high, arr);
    }
}

int main ()
{
  int arr[] = { 3, 2, 45, 6, 3, 56, 7, 8, 24 };
  quick (0, 8, arr);
  for (int i = 0; i <= 8; i++)
    {
      cout << arr[i] << "\t";
    }

  return 0;
}


selection


#include<iostream>
using namespace std;

void swap(int *x,int *y)
{
  int temp = *x;
     * x=*y;
      *y=temp;
}
int main()
{
 int a[]={3,8,1,6,2,10,12,20};
 int i,j,min;
 for(int i=0;i<7;i++)
 {
  min=i;
  for(int j=i+1;j<8;j++)
    if(a[min]>a[j])
       min=j;
   swap(&a[min],&a[i]);


 }
 cout<<"The array is";
 for(int i=0;i<8;i++)
  cout<<a[i]<<"\t";
return 0;
}
~


tower with modification


#include<iostream>
using namespace std;
int s=0,a=0,d=0;
int b[3]={0,0,0};
void tower(char S,char A,char D,int n)
{
 if(n==1)
 {
  cout<<"Move disk "<<n<<"form"<<S<<"to"<<D<<"\n";
  if(S=='S')
   s++;
  if(S=='A')
   a++;
  if(S=='D')
   d++;
  for(int i=0;i<n;i++)
   {
    if(i==(n-1))
     b[i]++;
   }
  return;
 }
tower(S,D,A,n-1);
  cout<<"Move disk "<<n<<"from"<<S<<"to"<<D<<"\n";
  for(int i=0;i<n;i++)
   {
    if(i==(n-1))
     b[i]++;
   }

 if(S=='S')
   s++;
  if(S=='A')
   a++;
  if(S=='D')
   d++;

 tower(A,S,D,n-1);

}

int main()
{
 tower('S','A','D',3);
 cout<<"The number of moves by S is\t"<<s<<"\n";
 cout<<"The number of moves by A is\t"<<a<<"\n";
 cout<<"The number of moves by D is\t"<<d<<"\n";
 for(int i=0;i<3;i++)
 {
  cout<<"The number of moves by\t"<<i+1<<"\t"<<"is\t"<<b[i]<<"\n";
 }
return 0;
}

                                           
