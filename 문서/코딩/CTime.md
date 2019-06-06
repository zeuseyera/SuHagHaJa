:kr: C/C++ 코딩(MFC)


## 1. COleDateTime

- 시간범위: 0 ~ 9999년

```
#include <ATLComTime.h>   // COleDateTime  
#include <afxstr.h>       // CString  
#include <stdlib.h>       // atoi  
```

### 1-1) 시각값 얻기

``` C++
COleDateTime	SiGak;

int Yeon = 1998;
int Wol = 1;
int Il  = 1;
int Si  = 0;
int Bun = 0;
int Cho = 0;

SiGak   = COleDateTime( Yeon, Wol, Il, Si, Bun, Cho );

int nJu = atoi( SiGak.Format( "%U" ) );
int nIl = SiGak.GetDayOfYear();

nIl     = SiGak.GetDay();

SiGak   = COleDateTime::GetCurrentTime();

nJu     = atoi( SiGak.Format( "%U" ) );

Yeon    = SiGak.GetYear();
nIl     = SiGak.GetDay();

Cho     = 1;
nJu     = atoi( SiGak.Format( "%U" ) );

```

## 2. CTime

- 시간범위: 1970 ~ 2038년

```
#include <atltime.h>   // CTime  
#include <afxstr.h>    // CString  
#include <stdlib.h>    // atoi  
```

### 2-1) 시각값 얻기

``` C++
CTime	SiGak;

int Yeon = 1998;
int Wol	= 1;
int Il	= 1;
int Si	= 0;
int Bun	= 0;
int Cho	= 0;

// 시각을 직접 설정하기
SiGak   = CTime( Yeon, Wol, Il, Si, Bun, Cho );

// 현재년도(SiGak)의 주차를 문자열로 받고 숫자로 변환하기
int nJu	= atoi( SiGak.Format( "%U" ) );

// 현재년도(SiGak)의 일차를 받기
int nIl	= SiGak.GetDayOfYear();

// 시각을 지정한 형식의 문자열로 받기
CString IlJa = SiGak.Format(_T("%Y%m%d"));	// 19010101

// 시스템에서 시각을 가져오기
SiGak   = CTime::GetCurrentTime();

nIl     = SiGak.GetDay();
nJu     = atoi( SiGak.Format( "%U" ) );

Yeon    = SiGak.GetYear();
nIl     = SiGak.GetDay();
nJu     = atoi( SiGak.Format( "%U" ) );


```

### 2-2) 시각을 문자열로 받는 방법, CTime => Format( "%a" )

``` C++
CTime	SiGak;
CString MunJa;

SiGak   = CTime::GetCurrentTime();
MunJa   = SiGak.Format( "%a" );

%F : 년-월-일 (00-00-00) // 현재 지역의 날짜, ISO
%X : 시:분:초 (00:00:00) // 현재 지역의 시간(24시간)
%T : 시:분:초 (00:00:00) // 현재 지역의 시간(24시간)
%R : 시:분 (00:00)       // 현재 지역의 시간
%r : 시:분:초 AM (00:00:00 AM) // 현재 지역의 시간

%Y : 년 (0000)   // 네자리 년도
%y : 년 (00~99)  // 두자리 년도
%G : 년 (0000)   // 네자리 년도, ISO
%g : 년 (00~99)  // 두자리 년도, ISO
%m : 월 (01~12)  // 고유순서(수)
%d : 일 (01~31)
%e : 일 (1~31)
%H : 시 (00~23)
%I : 시 (01~12)
%M : 분 (00~59)  // 고유순서(수)
%S : 초 (00~59)  // 고유순서(수)

%p : AM, PM ( 오전: AM, 오후: PM )

%j : 일순 (001~366) // 고유순서, 1월 1일 = 1 부터
%U : 주순 (00~53)   // 고유순서, 0주 부터 몇번째 주(일요일 시작)
%W : 주순 (00~53)   // 고유순서, 0주 부터 몇번째 주(월요일 시작)
%V : 주순 (01~53)   // 고유순서, ISO, 4일이상 포함시 1주
%w : 요일순 (0~6)   // 고유순서, 0 ~ 6 ( 일요일 ~ 토요일 )
%u : 요일순 (1~7)   // 고유순서, 1 ~ 7 ( 월요일 ~ 일요일 )

%x : 월/일/년 (00/00/00) // 지역형식 날짜
%D : 월/일/년 (00/00/00) // 날짜

%a : 주이름 (영문 3자)
%A : 주이름 (영문)
%b : 월이름 (영문 3자)
%h : 월이름 (영문 3자)
%B : 월이름 (영문)
%c : 주 월 일 시:분:초 년도 ( sat jun 1 01:02:01 2019 ) // 지역형식

%C : 세기 (00~99)   // 년도를 100으로 나누고 정수로 제한한다
%z : +0900 (+시분 ~ -시분) // GMT시간에 더할값 (시간대역 지역)
%Z : ??? => "´eCN¹I±¹ C￥AØ½A"  // 시간대 이름

```


