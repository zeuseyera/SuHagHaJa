:kr: C/C++ 코딩(MFC)



### CListBox

1. 목록상자의 선택속성 변경(대화창 리소스)

| 동작 |   |   |  
| --- | --- | --- |  
| Selection | Single    | 하나만 선택할수있다 |  
|           | Multiple  | 여러개 선택할수있다 |  
|           | Extended  |                   |  

2. 목록상자의 선택속성 변경(코드로 직접 지정)

| AddString( "문자열" ) | 목록에 문자열 추가 |  
| --- | --- |  
| DeleteString(index) | 목록에서 항목 삭제 |  
| GetCount() | 전체 항목 갯수를 얻는다. |  
| GetSelcount() | 선택된 항목 갯수 리턴 |  
| GetSel() | 선택된 것인지 아닌지를 리턴한다 -> 양수 = TRUE , 음수 => FALSE |  
| GetText(int index,문자열변수) | index 번째 문자열을 문자열 변수에 넣는다 |  
| FindStringExact(문자열) | 지정 문자열의 index 값 리턴 -> 없으면 리턴값 LB_ERR 반환 |  
| FindString( "a" ) | "a"로 시작하는 항목을 모두 찾는다. |  
| ResetCountent() | 모든 내용을 지운다. |


``` C++

DDX_Control( pDX, IDC_MOKROK_SANGJA, m_MokRok_SangJa );

SetProperty( IDC_MOKROK_SANGJA, LBS_MULTIPLESEL );
SetProperty( IDC_MOKROK_SANGJA, LBS_EXTENDEDSEL );


```

### CListCtrl

- `CListCtrl` 를 **지역변수**로 사용하면 메모리 최적화로 인해 데이타를 잃어버린다...

``` C++


```


