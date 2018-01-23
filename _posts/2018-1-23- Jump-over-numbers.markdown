---
layout:     post
title:      "jump over numbers"
subtitle:   ""
date:       2018-01-23 12:00:00
author:     "Hux"
header-img: "img/post-bg-android.jpg"
tags:
    - C++
    - 基础算法题
---
#非递归算法

int jump_over_numbers(const vector<int>& list) {
	
    int pos = 0;
    
    int ans = 0;
    
    while (pos < list.size()) {
    
        int curr_val = list[pos];
	
        if (curr_val == 0) {
	
            return -1;
        }
	
        ans++;
	
        pos += curr_val;
	
    }

    return ans;
    
}
#递归的典型错误


#include<iostream>
	
using namespace std;


void jump_over_numbers(vector<int> &list);
	
int main()

{

	int array[]={3,4,1,2,5,6,9,0,1,2,3,1};
	
	vector<int> list;
	
	int length = sizeof(array)/sizeof(array[0]);
	
	list.reserve(length);
	
	for(int i=0;i<length;i++)
	{
	
		list.push_back(array[i]);
		
	}
	jump_over_numbers(list);
	
	//for(vector<int>::iterator iter=list.begin();iter!=list.end();iter++)
	
	//{
		//cout<<iter<<endl;
		
	//	cout<<*iter<<endl;
	
	//}
	
}
void jump_over_numbers(vector<int> &list) {

	static int time=0;
	
    if(list[0]>list.capacity())
    
     cout<<time<<endl;
     
    if(list[0]==0)
    
     cout<<-1<<endl;
     
    else{
    
      time++;
      
      list[0]+=list[list[0]]; 
      
      jump_over_numbers(list);
      
    }
    
}
