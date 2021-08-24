---
layout: post
title: c++로 날짜 계산 프로그램 만들기!
categories: [study]
tags: [coding,c++]
---
영어는 빨리빨리 안읽혀서 다시 한글자료로 틀었다. 4-1에서 연습문제로 나온 달력 만들기 프로그램을 저장해두고자 post를 쓴다.

파이썬에서 class 개념은 배웠어서 훨씬 쉽게 접근한 것 같다. 아직까진 ;로 끝나는 거 빼곤 크게 틀리는 문법도 없는 것 같다.

8/23기준으로 +506일을 하면 2023-1-11이었다. ㅎㅎ...ㅎ.ㅎㅎㅎ..ㅎㅎ.ㅎ.훵

```{.cpp}
#include <iostream>

class Date {
int year_;
int month_; // 1 부터 12 까지.
int day_; // 1 부터 31 까지.

public:
void SetDate(int year, int month, int date){
year_=year;
month_=month;
day_=date;
}

int MaxDay(){
	int max_day;

	switch(month_){
		case 1:
		case 3:
		case 5:
		case 7:
		case 8:
		case 10:
		case 12:
			max_day=31;
			break;
		case 4:
		case 6:
		case 9:
		case 11:
			max_day=30;
			break;
		case 2:
			if (year_%4==0)
				max_day=29;			
			else 
				max_day=28;
			break;

		};
	return max_day;
}

void TidyDate(){

	while (1){

		int max_day=MaxDay();

		if (day_<=max_day){
			break;
		};

		day_-=max_day;
		++month_;

		while (month_>12){
			year_+=(month_/12);
			month_%=12;
			};
		};


	};




void AddDay(int inc){
		day_+=inc;
		TidyDate();
	}

void AddMonth(int inc){
		month_+=inc;
		TidyDate();
	}

void AddYear(int inc){
		year_+=inc;
		TidyDate();
	}

void ShowDate(){
		std::cout<<year_<<"년 "<<month_<<"월 "<<day_<<"일 입니다."<<std::endl;
}

};

int main() {
	Date date;
	date.SetDate(2021,8,23);
	date.AddDay(506);
	date.ShowDate();
return 0;
}
```
