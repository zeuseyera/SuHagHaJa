:kr: C/C++ 코딩(MFC)

출처: https://blockdmask.tistory.com/338

## C++ string 클래스

- 헤더파일: \<string>

``` C++

typedef basic_string< char, char_traits<char>, allocator<char> >
	string;
typedef basic_string< wchar_t, char_traits<wchar_t>, allocator<wchar_t> >
	wstring;

```

  목차

  [1. C++ string 클래스 생성방법](#생성방법)

  [2. C++ string 클래스 멤버함수](#멤버함수)

  - [at()](#at), [operator\[\]](#operator), [front()](#front), [back()](#back)  
  - [size()](#size), [length()](#length), [capacity()](#capacity), [resize()](#resize), [shrink_to_fit()](#shrink_to_fit), reserve(), clear(), empty()  
  - c_str(), substr(), replace(), compare(), copy(), find(), push_back(), pop_back()  
  - begin(), end()  
  - swap(), operator+  


  [3. C++ string 클래스 본보기1](#본보기1): (생성과 출력, 문자열 연결, push_back, pop_back)

  [4. C++ string 클래스 본보기2](#본보기2): (size, capacity, length, clear)

  [5. C++ string 클래스 본보기3](#본보기3): (substr, replace, swap)

  [6. C++ string 클래스 본보기4](#본보기4): (find, operator[], at, front, back)

  [7. C++ string 클래스 본보기5](#본보기5): (begin, end, copy, compare)

---  
<a name="생성방법"></a>

### 1. C++ string 클래스 생성방법.

- **`std::`** 를 생략하려면 **`using namespace std;`** 를(std 이름생략 사용) 선언한다.  

- string 클래스는 C언어의 char*, char[] 문자열과 달리, 문자열끝에 `\0`(문자열 끝을 알리는)이 없다.  

- 생성방법

```C++
string  MunJaYeol0( "문자0" );

string  MunJaYeol1;
MunJaYeol1  = "문자1"

string  MunJaYeol2( MunJaYeol1 );
MunJaYeol2  = MunJaYeol0 + MunJaYeol1;

string  MunJaYeol3( "문자0 " + MunJaYeol1 + " 문자2" );

int suYeon  = 2019;
string  MunJaYeol4( "서기 " + to_string( suYeon ) + "년" );

int suWol   = 12;
int suIl    = 25;

stringstream WolIl;
WolIl << suWol << "월 " << suIl << "일";

# to_stoi( "123" )  // 문자열을 숫자로...
# to_string( 123 )  // 숫자를 문자열로...

string  MunJaYeol5( "서기 " + to_string( suYeon ) + "년 " + WolIl.str() );

char* Mun = MunJaYeol5.c_str();
```

<a name="멤버함수"></a>

### 2. C++ string 클래스 멤버함수

**`std::string`** 클래스에는 문자열을 다루는 여러개의 멤버함수가 있다.

**string** 클래스를 아래처럼 미리 정의한 변수로 설명한다

```C++
string  MunJaYeol1  = "문자열";
string  MunJaYeol2  = "조작실험";
```

string 인자 접근, access 관련

<a name="at"></a>

#### 2-1) MunJaYeol1.at( WiChi )  

- 원형: **`char& at( size_t WiChi );`**  

- 설명: WiChi(순번)에 해당하는 문자를 반환한다.  
WiChi 는 0부터 시작한다. WiChi 가 문자열의 범위를 벗어나면 예외를 반환한다.  

- 본보기: MunJaYeol1.at( 0 ); //'B'를 리턴합니다

<a name="operator"></a>

#### 2-2) MunJaYeol1.operator[ WiChi ]

- 원형: **`char& operator[]( size_t WiChi );`**  
- 설명: C++ string은 일반 배열처럼 대괄호를 이용해서 string 인자에 접근할 수 있습니다.  
문자열의 WiChi 범위를 검사하지 않기 때문에 `at` 함수보다 빠르다. 하지만 예외를 뱉어내지 않습니다. WiChi는 0부터 시작한다. WiChi 번째 값을 반환합니다.  
- 본보기: MunJaYeol1[1]; //'l'를 리턴합니다.

<a name="front"></a>

#### 2-3) MunJaYeol1.front()

- 원형: **`char& front();`**  
- 설명: C++11부터 가능. string의 맨 앞 인자를 반환합니다.  
- 본보기: MunJaYeol1.front();    //'B'를 리턴합니다.

<a name="back"></a>

#### 2-4) MunJaYeol1.back()

- 원형: **`char& back();`**  
- 설명: C++11부터 가능. string의 맨 뒤 인자를 반환합니다.  
개인적으로 front는 모르겠지만 back은 참 좋은 멤버변수인것 같습니다. 우리가 string의 첫번째 인자를 가지려고 할때는 str1[0]을 인덱스로 집어 넣으면 되지만 끝부분은 대부분 다른 멤버변수에 저장을 해놓거나 잘 모르는 경우가 많습니다. 그렇기 때문에 back() 을 이용하면 편하게 맨 뒤 인자를 가지고 올 수 있습니다.  
- 본보기: MunJaYeol1.back(); //'K'를 리턴합니다.

<a name="size"></a>

#### 2-5) MunJaYeol1.size()


- 원형: **`size_t size() const;`**  
- 설명: string의 사이즈를 반환합니다.  
- 본보기: MunJaYeol1.size(); // "BlockDMask" 이므로 10을 반환합니다. 

<a name="length"></a>

#### 2-6) MunJaYeol1.length()

- 원형: **`size_t length() const;`**  
- 설명: string의 <b>길이를 반환</b>합니다. size() 함수와 같다고 생각하면 됩니다.  
- 본보기: MunJaYeol1.length();   // "BlockDMask" 이므로 10을 반환합니다.

<a name="capacity"></a>

#### 2-7) MunJaYeol1.capacity()

- 원형: **`size_t capacity() const;`**  
- 설명: string 객체에 할당된 메모리 크기(bytes)를 반환합니다.  
capacity는 vector의 capacity와 마찬가지로 스트링 길이가 증가할 수 있기 때문에, 메모리 할당을 size에 대비해서 여유롭게 합니다  
size가 capacity를 넘게 될때 새롭게 더 큰 capacity(메모리)를 할당합니다.  
- 본보기: MunJaYeol1.capacity(); // "BlockDMask" 길이는 10인데 capacity는 15 입니다.  
- 본보기: MunJaYeol2.capacity(); // "BlogBlogBLogBlog" 길이는 16인데 capacity는 31 입니다.

15 -> 31 이런식으로 스트링의 capacity가 넘어가는 것을 알 수 있습니다.  
길이가 10 인 스트링을 우리가 str1 += "a" 이런식으로 계속해서 길이를 늘리다가 16이 되는순간 기존의 capacity를 넘어가므로 더 큰 capacity를 할당하여서 스트링을 다루게 됩니다.


#### 2-7) MunJaYeol1.resize( GaeSu )

- 원형: void resize( size_t GaeSu );
- 원형: void resize( size_t GaeSu, char MunJa );

- 설명: MunJaYeol1(문자열) 메모리를 GaeSu(개수) 크기로 조정한다. 

  만약 지정한 크기가 이전 크기보다 작다면, 뒤쪽 문자열은 버린다. 

  만약 지정한 크기가 이전 크기보다 크다면, 추가할당된 메모리는 공백으로 채운다. 만약 MunJa(문자)를 지정하면 추가할당된 메모리를 MunJa(문자)로 채운다.


- 본보기:  MunJaYeol1.resize( 5 )    // "BlockDMask" -> "Block" 이 됩니다. size는 5입니다.  
- 본보기:  MunJaYeol1.resize( 6 )    // "Block" -> "Block " 가 됩니다. 빈칸이 있습니다. size는 6이 되었습니다.  
- 본보기 :  MunJaYeol1.resize(10, 'a') // "Block " -> "Block aaaa" 가 됩니다. 사이에 빈칸이 하나 있는거 보이시죠? 이전에 추가했던 그것입니다.  


#### 2-8) MunJaYeol1.shrink_to_fit()

- 원형 : void shrink_to_fit();

- 설명 : C++11 입니다. 이 함수는 스트링 길이에 비해 낭비되고 있는 capacity(메모리)를 줄이는 함수입니다. 

- 본보기 :  MunJaYeol2.resize(4);    // "BlogBlogBlogBlog" -> "Blog" 가 됩니다. 아까 capacity에서 보자면 길이가 16짜리 string의 capacity는 31 이었습니다.

- 본보기 :  MunJaYeol2.shrink_to_fit();    // "Blog" 처럼 길이가 4가 된 스트링의 capacity에 알맞게 str2의 capacity가 31에서 16으로 줄어들게 됩니다.


#### 2-9) MunJaYeol1.reserve( n );

- 원형 : void reserve(size_t n = 0);

- 설명 : 문자열을 넣기 전에 미리 "곧 n만큼의 크기의 스트링이 들어올거니까 그에 맞는 capacity를 할당해 달라"는 함수 입니다.

  이건 보통 파일을 읽을 때 사용을 하는데요, 3000자 짜리 파일을 우리가 읽게 된다하면, 파일에 있는 글을 한자씩 가지고 오게되는데 이게 while문에서 eof를 이용해서 파일의 끝 까지 읽게 됩니다. 이런 경우에는 미리 메모리를 할당해서, capacity가 사이즈에 맞게 계속 늘어나는 행위를 덜하게해서 성능저하를 줄이게 하는 것 입니다.

  만약에 reserve를 하지 않고 그냥 파일을 읽는다면 아마 이렇게 될 것 입니다. str += "글" 이렇게 계속 파일이 끝이 나올 때 까지 더해질 것이고, str의 길이가 16이 되면 새롭게 capacity를 늘리는 작업이 들어가서 비용이 들게되고, 또 str의 길이가 32가 되면 새롭게 capacity를 늘리는 작업이 들어가게 되고....... 계속 .... 계속.... 늘리는 작업을 하게 됩니다. 이런 비효율적인 작업을 하지 않게 하려고 미리 메모리 예약을 하는 것 입니다.

  쉽게 말해서 노래방에 2인실을 갔는데, 2명이 더와서 4인실을 갔는데 또 여러명이 와서 8인실을 가고 이렇게 사람들이 이동하는 동안 우리는 노래를 못부르고 시간이 줄잖아요. 컴퓨터도 마찬가지 입니다 한번 할당해 놓은 메모리를 또 추가로 할당한다는 것은 그만큼 비용이 생기게 됩니다.


#### 2-10)  MunJaYeol1.clear();

- 원형 : void clear();

- 설명 : 스트링에 들어있는 문자열을 지우는 함수입니다. 이때, size와 length는 0이 되고, capacity는 그대로 남게 됩니다.

- 본보기 :  MunJaYeol1.clear();    //"BlockDMask" -> "" 이 됩니다. size와 lenth는 0이 되고, capacity는 15 그대로 입니다. (메모리 해제가 아닌 문자열 값들을 삭제하는것)


#### 2-11)  MunJaYeol1.empty();

- 원형 : bool empty() const;

- 설명 : 스트링이 비었는지 확인하는 함수입니다. 비었으면 true를 반환합니다. 비었음의 기준은 size, length가 0인 것 입니다. capacity와는 관계가 없습니다.

- 본보기 : if( MunJaYeol1.empty()) { return true; }    //이런식으로 비었는지 확인하면됩니다. clear를 사용하고 empty를 사용하면 당연히 true 겠죠?


#### 2-12)  MunJaYeol1.c_str()

- 원형 : const char* c_str() const;

- 설명 : C++ 스타일의 string 문자열을 C스타일의 문자열로 변경해주는 함수입니다. 

- 본보기 : const char* arr =  MunJaYeol1.c_str();    // "BlockDMask"가 "BlockDMask\0"로 반환해 줍니다. C언어에서 처럼 사용할 수 있습니다.


#### 2-13)  MunJaYeol1.substr(....)

- 원형 : string substr(size_t index = 0, size_t len = npos) const;

- 설명 : string을 index 에서부터 len만큼 잘라서 반환하는 함수입니다. 스트링 짤라서 반환.

  두번째 인자의 len의 디폴트 npos가 의미하는 것은 "-1"입니다. size_t의 타입은 unsigned int 타입입니다.

  그 unsigned int에 -1이 들어온다? 그게 무슨의미 일까요? 맞습니다.

  "언더플로우" 입니다. unsigned인 타입에 음수를 넣으면 제일 큰 값으로 세팅이 됩니다. 

  그렇기 때문에 npos에는 -1을 넣어서, 아무것도 넣지 않았을때는 항상 문자열이 길어질 수 있는 최대의 길이를 나타내게 됩니다.

- 본보기 :  MunJaYeol1.substr();          //"BlockDMask" 그대로 반환합니다.

- 본보기 :  MunJaYeol1.substr(5);        // "DMask"를 반환합니다. 0부터 세기 시작해서 "5" 번째 인자부터 끝까지의 문자열을 반환합니다.

- 본보기 :  MunJaYeol1.substr(5, 1);     // "D"를 반환합니다. 5번째 인자부터, 1의 길이만큼 문자열을 반환합니다.


#### 2-14)  MunJaYeol1.replace(....)

- 원형 : string& replace(size_t index, size_t len, const string& str)

- 설명 : 함수를 호출하는 문자열의 index위치에서 len 길이까지의 범위를 매개변수로 들어온 str 전체로 대체 하는 함수입니다.

- 본보기 :  MunJaYeol1.replace(5, 2, str2);

// "BlockDMask"의 5번째 인자에서부터 2개를 str2로 대체하게 됩니다. 그러면 "BlockBlogBlogBlogBlogask" 이런식의 문자가 됩니다.


#### 2-15)  MunJaYeol1.compare(....)
- 원형 : int compare(const string& str) const;

- 원형 : int compare(size_t index, size_t len, const string& str) const;

- 설명 : 매개변수로 들어온 str을 비교해서 같으면 0을 반환하고, 다르면 0이 아닌 값을 반환하는 함수입니다.

  호출하는 스트링의 값이 매개변수로 들어온 스트링의 값보다 작을때(사전순 빠를때) 음수(-1)를 반환하고

  호출하는 스트링의 값이 매개변수로 들어온 스트링의 값보다 클때(사전순 느릴때) 양수(1)를 반환합니다

- 본보기 :  MunJaYeol1.compare(str2);    // "BlockDMask", "BlogBlogBLogBLog"는 같지 않기 때문에 0이 아닌 값을 반환하고, Blo까지는 둘이 똑같고, 그다음 c, g를 비교하게 됩니다. 이때, c가 g보다 사전상 더 앞선글자이기 때문에 c가 더 작은 글자가 됩니다. 그렇기 때문에 음수(-1)를 반환하게 됩니다.

- 본보기 :  MunJaYeol2.compare(str1);    // 이거는 그럼 양수(1)을 반환하겠죠?

- 본보기 :  MunJaYeol1.compare("BlockDMask");    //이 경우에는 두 스트링이 같기 때문에 0을 반환합니다.

- 본보기 :  MunJaYeol1.compare(0, 2, str2);    //"BlockDMask"와 "BlogBlogBlogBlog" 스트링의 0번째 인덱스부터 2번째 인덱스까지 하면, "Blo"가 같기 때문에 0을 반환합니다.


#### 2-16)  MunJaYeol1.copy(....)

- 원형 : size_t copy(char* arr, size_t len, size_t index = 0) const;

- 설명 : 딱봐도 복사를 하는 함수입니다. 이거는 특이하게 길이는 나타내는 len이 두번째고, index가 세번째 인자입니다. 아무래도 시작하는곳이 더 중요하지 않다고 판단하고 디폴트 인자를 설정해주려고 맨뒤로 보낸걸로 보입니다.

  첫번째 매개변수 : 호출한 문자열을 첫번째 매개변수 문자열에 복사하는 함수입니다. char* 인걸 보면, C언어의 문자열(배열타입)을 받습니다.

  두번째 매개변수는 복사할 문자열의 길이를 나타냅니다.

  세번째 매개변수는 복사를 시작할 위치 입니다. index는 0부터 시작하는거 아시죠?

  마지막으로 실제로 복사된 길이, arr의 길이를 반환합니다.

- 본보기 : char arr[10];    //문자열을 복사해서 넣을 빈 배열을 만듭니다.

- 본보기 : int arrLen =  MunJaYeol1.copy(arr, 3, 5);    //5번째 index부터 3의 길이만큼 복사 한다는 거니까 "BlockDMask" 빨간 부분이 들어갔을겁니다. 그리고 반환하는 arrLen은 3의 길이겠죠?

- 본보기 : arr[arrLen] = '\0';    //그리고 C의 문자열의 끝에는 '\0'이걸 넣어주어야 합니다. 그러면 문자열 복사가 깔끔하게 되었을 겁니다.


#### 2-17)  MunJaYeol1.find(....)

- 원형 : size_t find (const string& str, size_t index = 0) const;

- 원형 : size_t find (const char* arr, size_t index = 0) const;

- 설명 : 매개변수로 들어온 문자열과, 내 문자열중에 일치하는 게 있는지 확인하는 함수입니다. 

  만약에 일치하는게 있다면, 일치하는 부분의 첫번째 순서(index)를 반환합니다.

  두번째 매개변수로 들어온 index는 어느 위치에서 부터 찾을까 입니다.

- 본보기 :  MunJaYeol2.find("Blog");    // 0 을 반환합니다.

- 본보기 :  MunJaYeol2.find("Blog", 5);    // 5번째 인자부터 blog를 찾게되니 BlogBlogBlogBlog 빨간색 l에서부터 찾게되므로 그 다음에 나오는 b의 위치인 8을 반환할 것 입니다.


#### 2-18)  MunJaYeol1.push_back(c)

- 원형 : void push_back(char c);

- 설명 : 함수를 호출하는 스트링의 맨뒤에 문자 c를 더하는 함수 입니다.

- 본보기 :  MunJaYeol1.push_back('a');    //"BlockDMask" -> "BlockDMaska" 'a'가 하나 더해집니다.


#### 2-19)  MunJaYeol1.pop_back()

- 원형 : void pop_back()

- 설명 : 함수를 호출하는 스트링의 맨뒤에 있는 문자 하나를 없애는 함수 입니다.

- 본보기 :  MunJaYeol1.pop_back();    // "BlockDMask" -> "BlockDMas" 이렇게 k가 하나 빠집니다.


#### 2-20)  MunJaYeol1.begin();

- 원형 : iterator begin();

- 원형 : const_iterator begin() const;

- 설명 : 문자열의 첫 번째 문자를 가리키는 반복자(iterator 포인터)를 반환합니다.


#### 2-21)  MunJaYeol1.end();

- 원형 : iterator end();

- 원형 : const_iterator end() const;

- 설명 : 문자열의 마지막의 바로 다음을 가리키는 반복자(iterator 포인터)를 반환합니다. (잘 봐야해요 문자열 끝이 아니라 그 다음!)


iterator는 보통 순회를 할때 많이 사용합니다. 아래와 같은 방식으로 많이 쓰죠.

아래와 같이 하면, B 엔터 l 엔터 이런식으로 한글자씩 나오게 됩니다.

```C++
for ( string::iterator iter = MunJaYeol1.begin(); iter !=  MunJaYeol1.end(); ++iter )
{
  cout << *iter << endl;
}
```


#### 2-22) swap(str1, str2);

- 원형 : void swap(string& str1, string& str2);

- 설명 : str1과 str2를 바꾸는 것 입니다. 

  스왑을 할때 복사를 해서 스왑을 하는것이 아니라 서로 참조(reference)를 교환해서 스왑을 합니다. 

  그렇기 때문에 복사에 의한 성능저하를 우려할 필요가 없습니다.

- 본보기 : swap(str1, str2);    //str1이 "blog~~"가 되고, str2가 "BlockDMask"가 됩니다.


▶ operator+

- 설명 : 이거는 오퍼레이터 +인데요. string끼리 더할 수 있습니다. 더한다는 의미는 이어 붙인다는 것 입니다.

  이미 만들어져 있는 것이라, 우리가 그냥 string끼리 더해서 사용하면 됩니다. 

- 본보기 : str1 += str2;    //str1은 "BlockDMaskBlogBlogBlogBlog" 이런식으로 만들어집니다.


<a name="본보기1"></a>

### 3. C++ string 클래스 본보기1

> 생성과 출력, 문자열 연결, push_back, pop_back

```C++
//C++ string example1
#include <iostream>
#include <string>
using namespace std;
 
int main()
{
  string str1 = "BlockDMask";
  string str2("BlogBlogBlogBlog");
  string str3(str1);
 
  //string을 생성하는 다양한 방법.
  cout << "==> onstructor" << endl;
  cout << "str1 = \"BlockDMask\" \n : " << str1 << endl << endl;
  cout << "str2(\"BlogBlogBlogBlog\") \n : " << str2 << endl << endl;
  cout << "str3(str1) \n : " << str3 << endl << endl;
 
  //push_back, pop_back
  cout << endl;
  cout << "==> string front, back example." << endl;
  MunJaYeol1.push_back('1');
  cout << " MunJaYeol1.push_back('1') : " << str1 << endl;
  MunJaYeol1.push_back('2');
  cout << " MunJaYeol1.push_back('2') : " << str1 << endl;
  MunJaYeol1.pop_back();
  cout << " MunJaYeol1.pop_back() :  " << str1 << endl;
  MunJaYeol1.pop_back();
  cout << " MunJaYeol1.pop_back() :  " << str1 << endl;
  MunJaYeol1.pop_back();
  cout << " MunJaYeol1.pop_back() :  " << str1 << endl;
 
  //operator+ stirng 덧셈.
  cout << endl;
  cout << "==> str1 += str2" << endl;
  str1 += str2;
  cout << str1 << endl;
           
  cout << endl;
  system("pause");

  return 0;
}

```

▲ C++ string 예제1 (생성과 출력, 문자열 연결, push_back, pop_back)

stirng을 생성하는 3가지 방법에 대한 예제

그리고 string끼리 연결하기, 더하기, 맨뒤에 문자 추가하기, 맨뒤에있는 문자 뺴기


<a name="본보기2"></a>

### 4. C++ string 클래스 본보기2

> size, capacity, length, clear, shrink_to_fit

```C++
//C++ string example2
#include <iostream>
#include <string>
using namespace std;
 
int main()
{
    string str2 = "BlogBlogBlogBlog";
 
    cout << "==> str2 original" << endl;
    cout << "str2 : " << str2 << endl;
    cout << " MunJaYeol2.size() : " <<  MunJaYeol2.size() << endl;
    cout << " MunJaYeol2.length() : " <<  MunJaYeol2.length() << endl;
    cout << " MunJaYeol2.capacity() : " <<  MunJaYeol2.capacity() << endl;
    
    cout << endl;
    MunJaYeol2.resize(4);
    cout << "==>  MunJaYeol2.resize(4)" << endl;
    cout << "str2 : " << str2 << endl;
    cout << " MunJaYeol2.size() : " <<  MunJaYeol2.size() << endl;
    cout << " MunJaYeol2.length() : " <<  MunJaYeol2.length() << endl;
    cout << " MunJaYeol2.capacity() : " <<  MunJaYeol2.capacity() << endl;
 
    cout << endl;
    MunJaYeol2.shrink_to_fit();
    cout << "==>  MunJaYeol2.shrink_to_fit()" << endl;
    cout << "str2 : " << str2 << endl;
    cout << " MunJaYeol2.size() : " <<  MunJaYeol2.size() << endl;
    cout << " MunJaYeol2.length() : " <<  MunJaYeol2.length() << endl;
    cout << " MunJaYeol2.capacity() : " <<  MunJaYeol2.capacity() << endl;
 
    cout << endl;
    MunJaYeol2.clear();
    cout << "==>  MunJaYeol2.clear()" << endl;
    cout << "str2 : " << str2 << endl;
    cout << " MunJaYeol2.size() : " <<  MunJaYeol2.size() << endl;
    cout << " MunJaYeol2.length() : " <<  MunJaYeol2.length() << endl;
    cout << " MunJaYeol2.capacity() : " <<  MunJaYeol2.capacity() << endl;
 
    cout << endl;
    system("pause");

    return 0;
}

```

<a name="본보기3"></a>

### 5. C++ string 클래스 본보기3

> substr, replace, swap

```C++
//C++ string example3.
#include <iostream>
#include <string>
using namespace std;
 
int main()
{
    string str1 = "BlockDMask";
    string str2 = "BlogBlogBlogBlog";
 
    cout << "str1 : " << str1 << endl;
    cout << "str2 : " << str2 << endl;
    cout << endl;
    
    //string substr example.
    cout << " MunJaYeol1.substr(5) : " <<  MunJaYeol1.substr(5) << endl;
    cout << " MunJaYeol1.substr(5,1) : " <<  MunJaYeol1.substr(5,1) << endl;
    
    //string replace example.
    cout << " MunJaYeol1.replace(5, 2, str2) : " <<  MunJaYeol1.replace(5, 2, str2) << endl;
 
    //string swap example.
    cout << endl;
    string str3 = "C++ example";
    cout << "str2 : " << str2 << endl;
    cout << "str3 : " << str3 << endl;
 
    cout << endl;
    cout << "swap(str2, str3)" << endl;
    cout << "str2 : " << str2 << endl;
    cout << "str3 : " << str3 << endl;
 
    cout << endl;
    system("pause");
    return 0;
}

```

<a name="본보기4"></a>

### 6. C++ string 클래스 본보기4

> find, operaotr[], at, front, back

```C++
//C++ string example4.
#include <iostream>
#include <string>
using namespace std;
 
int main()
{
    string str1 = "BlockDMask";
    string str2 = "BlogBlogBlogBlog";
 
    cout << "str1 : " << str1 << endl;
    cout << "str2 : " << str2 << endl;
    cout << endl;
 
    //find
    cout << "==> string find example." << endl;
    cout << " MunJaYeol1.find(\"DM\") : " <<  MunJaYeol1.find("DM") << endl;
    cout << " MunJaYeol2.find(\"Blog\") : " <<  MunJaYeol2.find("Blog") << endl;
    cout << " MunJaYeol2.find(\"Blog\", 5) : " <<  MunJaYeol2.find("Blog", 5) << endl;
 
    //operator[], at
    cout << endl;
    cout << "==> string operator[], at() example." << endl;
    cout << "str1[0] : " << str1[0] << endl;
    cout << "str1[3] : " << str1[3] << endl;
    cout << "str1[ MunJaYeol1.size()-1] : " << str1[ MunJaYeol1.size() - 1] << endl;
    cout << endl;
    cout << " MunJaYeol1.at(0) : " <<  MunJaYeol1.at(0) << endl;
    cout << " MunJaYeol1.at(3) : " <<  MunJaYeol1.at(3) << endl;
    cout << " MunJaYeol1.at( MunJaYeol1.size()-1) : " <<  MunJaYeol1.at( MunJaYeol1.size() - 1) << endl;
 
    //front, back
    cout << endl;
    cout << "==> string front, back example." << endl;
    cout << "str1[0] : " << str1[0] << endl;
    cout << " MunJaYeol1.at(0) : " <<  MunJaYeol1.at(0) << endl;
    cout << " MunJaYeol1.front() : " <<  MunJaYeol1.front() << endl;
    cout << endl;
    cout << "str1[ MunJaYeol1.size()-1] : " << str1[ MunJaYeol1.size() - 1] << endl;
    cout << " MunJaYeol1.at( MunJaYeol1.size()-1) : " <<  MunJaYeol1.at( MunJaYeol1.size() - 1) << endl;
    cout << " MunJaYeol1.back() : " <<  MunJaYeol1.back() << endl;
 
    cout << endl;
    system("pause");
    return 0;
}

```

<a name="본보기5"></a>

### 7. C++ string 클래스 본보기5

> begin, end, copy, compare

```C++
//C++ string example5
#include <iostream>
#include <string>
using namespace std;
 
int main()
{
    string str1 = "BlockDMask";
    string str2 = "BlogBlogBlogBloc";
 
    cout << "str1 : " << str1 << endl;
    cout << "str2 : " << str2 << endl;
    cout << endl;
 
    //begin, end
    cout << "==> begin, end" << endl;
    string::iterator iter =  MunJaYeol1.begin();
    for ( ; iter !=  MunJaYeol1.end(); ++iter )
    {
        cout << *iter << " ";
    }
    cout << endl;
 
    //copy
    cout << endl;
    cout << "==> copy " << endl;
    char arr[10];
    int arrLen =  MunJaYeol1.copy(arr, 3, 5);
    cout << " MunJaYeol1.copy(arr, 3, 5)" << endl;
    cout << "arrLen : " << arrLen << endl;
    cout << arr << endl;    //error.
    arr[arrLen] = '\0';
    cout << arr << endl;    //ok.
 
    //compare
    cout << endl;
    cout << "==> compare" << endl;
    cout << " MunJaYeol1.compare(\"BlockDMask\") : " <<  MunJaYeol1.compare("BlockDMask") << endl;
    cout << " MunJaYeol1.compare(str2) : " <<  MunJaYeol1.compare(str2) << endl;
    cout << " MunJaYeol2.compare(str1) : " <<  MunJaYeol2.compare(str1) << endl;
    cout << endl;
    system("pause");
    return 0;
}

```

