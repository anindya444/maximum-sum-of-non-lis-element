# maximum-sum-of-non-lis-element
#include<iostream>
#include<vector>
#include<numeric>
#include<climits>
using namespace std;


int main(){
 vector<int>arr = {8,4,5,7,1,2,3};
int n=arr.size();
vector<vector<int>>d(n,vector<int>(2));
for(int i=0;i<n;++i)
{     d[i][0]=arr[i];
      d[i][1]=1;   
for(int j=0;j<i;++j){

    if ( arr[i]>arr[j]){
        if(d[j][1]+1==d[i][1]){d[i][0]=min (d[i][0],d[j][0]+arr[i]);}
    
  else if(d[j][1]+1>d[i][1]){
    d[i][0]=d[j][0]+arr[i];
    d[i][1]=d[j][1]+1;
                            }  
     }
   }
}
int maxlen=0;
for(int i=0;i<n;i++){
    maxlen=max(maxlen,d[i][1]);
}
int minsum=INT_MAX;
for(int i=0;i<n;++i){
    if(d[i][1]==maxlen){
        minsum=min(minsum,d[i][0]);}
    }

    int total=accumulate(arr.begin(),arr.end(),0);
    cout<< total-minsum<<endl;
     for(int i=0;i<d.size();++i)
    {
        for(int j=0;j<d[i].size();++j)
        {cout<<d[i][j]<<" ";}cout<<endl;
    }
}

