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

- 

``` C++


```

#### CListCtrl 확장양식

| 양식 | 가능 버전 | 설명 |  
| --- | --- | --- |  
| LVS_EX_AUTOAUTOARRANGE | Vista | 자동으로 아이콘을 정리해 준다. |  
| LVS_EX_AUTOCHECKSELECT | Vista | 자동으로 체크박스의 클릭을 지원해 준다. |  
| LVS_EX_AUTOSIZECOLUMNS | Vista | 컬럼의 크기를 자동으로 맞춰준다. |  
| LVS_EX_BORDERSELECT | 4.71 | 항목이 강조되는 항목이 아닌 항목 변화의 테두리 색상을 선택 |  
| LVS_EX_CHECKBOXES | 4.70 | 목록보기에 체크 박스를 사용 할 수 있게 된다.
| LVS_EX_COLUMNOVERFLOW |  | 상징/목록보기에서 상징이 화면에 다 나타나지 못할 경우 LVN_COLUMNOVERFLOWCLICK 통지메세지 발생 시켜준다. LVS_EX_HEADERINALLVIEWS 양식이 적용되어 있는 상태에서만 사용가능한 양식이다. |  
| LVS_EX_COLUMNSNAPPOINTS | Vista | 사용자가 열크기조정 할때 최소열너비에 맞춘다. |  
| LVS_EX_DOUBLEBUFFER | 6.00 | 깜빡임을 최소화 하기 위하여 이중버퍼링을 사용한다. |  
| LVS_EX_FLATSB | 4.71 | 목록보기에서 flat scroll bar 를 활성화 시킨다. |  
| LVS_EX_FULLROWSELECT | 4.70 | 항목이 선택될 때 항목과 하위항목을 같이 강조한다. (한줄 전체 선택) |  
| LVS_EX_GRIDLINES | 4.70 | 테두리를 보여준다. |  
| LVS_EX_HEADERDRAGDROP | 4.70 | 헤더를 드래그 해서 순서를 바꿀수 있게 해준다. |  
| LVS_EX_HEADERINALLVIEWS | Vista | 모든 보기 모드에서 컬럼 헤더를 보여준다. |  
| LVS_EX_HIDELABELS | Vista | 상징/작은상징 보기에서 레이블을 숨긴다. |  
| LVS_EX_INFOTIP | 4.71 | LVN_GETINFOTIP 통지 메세지를 부모 윈도우에게 보내 아이템의 툴팁을 보여준다. |  
| LVS_EX_JUSTIFYCOLUMNS | Vista | 상징은 전체보기를 사용한 열로 정렬한다. |  
| LVS_EX_LABELTIP | 5.80 | 툴팁의 숨겨진 레이블을 펼친다. 이 스타일을 적용 안하면 큰 아이콘 모드에서만 숨겨진 레이블을 펼친다. |  
| LVS_EX_MULTIWORKAREAS | 4.71 | 만약 목록보기제어를 LVS_AUTOARRANGE 양식으로 정했다면, 작업영역이 하나 이상 정의될 때까지 자동정렬을 제어하지 않는다.(LVM_SETWORKAREAS 를 보라). 효과를 적용하기 위해, 이 양식은 반드시 제어에 모든 작업영역이 정의되고 모든 항목이 추가되기 전에 설정해야 한다. |  
| LVS_EX_ONECLICKACTIVATE | 4.70 | 한번 클릭으로 활성화 시킨다. |  
| LVS_EX_REGIONAL | 4.71 | SetWindowRgn 를 사용한 상징과 글자 항목만 포함하기 위해 목록보기창 영역을 설정한다. 항목이 아닌 모든 영역은 창영역에서 제외된다. 이 양식은 LVS_ICON 양식을 사용한 목록보기 제어에서만 가능하다. |  
| LVS_EX_SIMPLESELECT | 6.00 | 아이콘보기에서 큰 아이콘 렌더링의 상단 오른쪽에있는 컨트롤의 상태 이미지를 이동합니다 |  
| LVS_EX_SINGLEROW | Vista | 사용하지 않는다. |  
| LVS_EX_SNAPTOGRID | Vista | 아이콘 보기에서 아이콘이 자동으로 격자에 맞춰진다. |  
| LVS_EX_SUBITEMIMAGES | 4.70 | 서브 아이템도 이미지를 사용할 수 있게 된다. |  
| LVS_EX_TRACKSELECT | 4.70 | 마우스로 아이템을 클릭하지 않아도 마우스 커서를 갖다 대면 자동으로 선택되게 한다. |  
| LVS_EX_TRANSPARENTBKGND | Vista | 배경을 부모 윈도우의 WM_PRINTCLIENT 에서 그린다. |  
| LVS_EX_TRANSPARENTSHADOWTEXT | Vista | 배경이 투명할때 텍스트에 그림자를 준다. |  
| LVS_EX_TWOCLICKACTIVATE | 4.70 | 두번 클릭하여 활성화 시킨다. |  
| LVS_EX_UNDERLINECOLD | 4.71 | LVS_EX_TWOCLICKACTIVATE 스타일에서 사용하는 스타일로 활성화 될 수 있는 항목을 밑줄로 보여주되 핫 항목에는 밑줄을 그어주지 않는다. |  
| LVS_EX_UNDERLINEHOT | 4.71 | LVS_EX_ONECLICKACTIVATE 스타일과 같이 사용하며 마우스가 오버되있는 아이템에 밑줄을 그어주어 활성화 후보를 알려주는 시각적 효과이다. |  



