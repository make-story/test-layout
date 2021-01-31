# HTML Layout 정리   

Flex 는 한 방향 레이아웃 시스템이고 (1차원)  
Grid 는 두 방향(가로-세로) 레이아웃 시스템 (2차원)  

> 참고페이지  
https://studiomeal.com/archives/197  
https://studiomeal.com/archives/533  

-----

## Grid  
- 그리드는 판면을 수직과 수평으로 분할하여 디자인하거나 편집하여 레이아웃을 잡는 작업을 도와주며 결국 인쇄물의 시각적 질서와 일관성을 유지시키는 필수적인 도구  
그리드 시스템은 1940년대에 스위스에서 개발되어 처음 사용  
격자, 바둑판의 눈금 또는 동일하게 주어진 좌표를 수직과 수평으로 일정하게 나누는 망을 말함  
그리드를 통해 시각적인 질서와 일관성을 유지시키고, 조화롭게 보일 수 있도록 하는 것이 목적  
  
- 왜 그리드 시스템을 사용해야 하는가?  
`잘 디자인된 그리드 시스템은 더 많이 아름답게 읽어 내려갈 수 있습니다.`  
한 화면에 `다양한(수 많은) 컨텐츠를 보여줄 때,` 레이아웃에 대한 `'기준'과 '규칙'`이 없다면  
사용자에게 정리되지 않은 것들을 보여주며 정리해서 보라고 강요하는 것과 같다.  
화면 레이아웃을 설계하는 개발자 입장에서도 그리드시스템은 디자이너와의 협업, 반응형웹에 대한 대응이 보다 쉬워진다.  
  
- 참고자료  
https://960.gs/  
https://morioh.com/p/c1c5fca4d95e  
https://brunch.co.kr/@refreshstudio/10  
http://news.samsungdisplay.com/15024  
https://brunch.co.kr/@blackindigo-red/8  

-----

### Grid 용어

- 그리드 컨테이너 (Grid Container)
display: grid 를 적용하는, `Grid의 전체 영역 (Grid 를 감싸는 것)`  
Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 됨  

- 그리드 아이템 (Grid Item)
Grid 컨테이너의 `자식 요소들`
이 아이템들이 Grid 규칙에 의해 배치 됨   

- 그리드 트랙 (Grid Track)
Grid의 `행(Row) 또는 열(Column)`  

- 그리드 셀 (Grid Cell)
Grid의 `한 칸`을 가리킴

- 그리드 라인(Grid Line)
Grid `셀을 구분하는 선`  

- 그리드 번호(Grid Number)
Grid `라인의 각 번호`  

- 그리드 갭(Grid Gap)
Grid `셀 사이의 간격`  

- 그리드 영역(Grid Area)
Grid `라인으로 둘러싸인 사각형 영역`으로, 그리드 셀의 집합    

-----

### Grid 구현
`IE 의 경우 -ms- 프리픽스 필요`

```html
<!-- div.container - Grid Container(그리드 컨테이너) -->
<div class="container">
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">A</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">B</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">C</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">D</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">E</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">F</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">G</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">H</div>
	<!-- div.item - Grid Item(그리드 아이템) -->
	<div class="item">I</div>
</div>
```

```css
.container {
	display: grid;
	/* display: inline-grid; */
}
```

-----

### 그리드 형태 정의  
컨테이너에 Grid 트랙의 크기들을 지정해주는 속성  

grid-template-rows   
grid-template-columns   
```css
.container {
	/* 행(row)의 배치 */
	grid-template-columns: 200px 200px 500px;
	/* grid-template-columns: 1fr 1fr 1fr */ /* 1:1:1 비율인 3개의 column을 만들겠다는 의미 */
	/* grid-template-columns: repeat(3, 1fr) */
	/* grid-template-columns: 200px 1fr */
	/* grid-template-columns: 100px 200px auto */

	/* 열(column)의 배치 */
	grid-template-rows: 200px 200px 500px;
	/* grid-template-rows: 1fr 1fr 1fr */ /* 1:1:1 비율인 3개의 rows를 만들겠다는 의미 */
	/* grid-template-rows: repeat(3, 1fr) */
	/* grid-template-rows: 200px 1fr */
	/* grid-template-rows: 100px 200px auto */
}
```

> fr은 fraction, 숫자 비율대로 트랙의 크기를 나눕니다.  

-----

### repeat 함수  
repeat는 반복되는 값을 자동으로 처리할 수 있는 함수  

repeat(반복횟수, 반복값)  

```css
.container {
	grid-template-columns: repeat(5, 1fr); /* 1fr 1fr 1fr 1fr 1fr 와 같은 값 */

	/* grid-template-columns: repeat(3, 1fr 4fr 2fr); */
}
```

-----

### minmax 함수  
최솟값과 최댓값을 지정할 수 있는 함수  

minmax(100px, auto)의 의미는 최소한 100px, 최대는 자동으로(auto)  

```css
.container {
	grid-template-columns: repeat(3, 1fr);
	grid-template-rows: repeat(3, minmax(100px, auto));
}
```

-----

### auto-fill 과 auto-fit  
auto-fill 과 auto-fit 은 column의 개수를 미리 정하지 않고,  
설정된 너비가 허용하는 한 최대한 셀을 채움  

```css
.container {
	grid-template-columns: repeat(auto-fill, minmax(20%, auto)); /* auto-fill 의 크기를 20% 로 설정했으므로, 1개의 row 에는 5개의 셀이 들어감 */
}
```

-----

### 간격 만들기
그리드 셀 사이의 간격을 설정  

row-gap  
column-gap  
gap  

```css
.container {
	row-gap: 10px; /* row 의 간격을 10px 로 */
	column-gap: 20px; /* column 의 간격을 20px 로 */
}
```
```css
.container {
	gap: 10px 20px; /* row-gap: 10px; column-gap: 20px; */
}
```
```css
.container {
	gap: 20px; /* row-gap: 20px; column-gap: 20px; */
}
```

> IE 에서는 gap 의 대체 속성이 없음  

-----

### 그리드 형태를 자동으로 정의  

grid-auto-columns  
grid-auto-rows  
(아이템 개수를 알 수 없을 때 유용)  

```css
.container {
	grid-auto-rows: minmax(100px, auto);
}
```

-----

### 각 셀의 영역 지정  
Grid 아이템에 적용하는 속성으로, 각 셀의 영역을 지정  

grid-column-start  
grid-column-end  
grid-column  
grid-row-start  
grid-row-end  
grid-row   

column 으로 살펴보면, grid-column-start가 시작 번호, grid-column-end가 끝 번호  
```css
.item:nth-child(1) {
	grid-column-start: 1;
	grid-column-end: 3;
	grid-row-start: 1;
	grid-row-end: 2;
}
```

시작번호 / 끝번호를 지정하는 방법 외에, `몇 개의 셀을 차지하게 할 것인지를 지정 가능`  
```css
.item:nth-child(1) {
	/* 1번 라인에서 2칸 */
	grid-column: 1 / span 2;
	/* 1번 라인에서 3칸 */
	grid-row: 1 / span 3;
}
```

-----

### 영역 이름으로 그리드 정의  
각 영역(Grid Area)에 이름을 붙이고, 그 이름을 이용해서 배치하는 방법(직관적인 방법)    

grid-template-areas  

```css
.container {
	grid-template-areas:
		/* 각자 차지하는 셀의 개수만큼 해당 위치에 이름을 써주면 됩니다. */
		"header header header"
		"   a    main    b   "
		"   .     .      .   "
		"footer footer footer";
}
```

각 영역의 이름은 해당 아이템 요소에 grid-area 속성으로 이름 매칭
```css
.header { grid-area: header; }
.sidebar-a { grid-area: a; }
.main-content { grid-area: main; }
.sidebar-b { grid-area: b; }
.footer { grid-area: footer; }
```

-----

### 자동 배치  
아이템이 자동 배치되는 흐름을 결정하는 속성  

grid-auto-flow  

```css
.container {
	display: grid;
	grid-template-columns: repeat(auto-fill, minmax(25%, auto));
	grid-template-rows: repeat(5, minmax(50px,auto));
	grid-auto-flow: dense;
}
.item:nth-child(2) { grid-column: auto / span 3; }
.item:nth-child(5) { grid-column: auto / span 3; }
.item:nth-child(7) { grid-column: auto / span 2; }
```

-----

### 세로 방향 정렬  
아이템들을 세로(column축) 방향으로 정렬   
컨테이너에 적용  

align-items  

```css
.container {
	align-items: stretch;
	/* align-items: start; */
	/* align-items: center; */
	/* align-items: end; */
}
```

### 가로 방향 정렬  
아이템들을 가로(row축) 방향으로 정렬   
컨테이너에 적용  

justify-items  

```css
.container {
	justify-items: stretch;
	/* justify-items: start; */
	/* justify-items: center; */
	/* justify-items: end; */
}
```

### place-items
align-items와 justify-items를 같이 쓸 수 있는 단축 속성  
align-items, justify-items의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용  

```css
.container {
	place-items: center start;
}
```

-----

### 아이템 그룹 세로 정렬  
Grid 아이템들의 높이를 모두 합한 값이 Grid 컨테이너의 높이보다 작을 때 Grid 아이템들을 통째로 정렬   

align-content  

```css
.container {
	align-content: stretch;
	/* align-content: start; */
	/* align-content: center; */
	/* align-content: end; */
	/* align-content: space-between; */
	/* align-content: space-around; */
	/* align-content: space-evenly; */
}
```

### 아이템 그룹 가로 정렬   
Grid 아이템들의 너비를 모두 합한 값이 Grid 컨테이너의 너비보다 작을 때 Grid 아이템들을 통째로 정렬  

justify-content  

```css
.container {
	justify-content: stretch;
	/* justify-content: start; */
	/* justify-content: center; */
	/* justify-content: end; */
	/* justify-content: space-between; */
	/* justify-content: space-around; */
	/* justify-content: space-evenly; */
}
```

### place-content
align-content와 justify-content를 같이 쓸 수 있는 단축 속성  
align-content, justify-content의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용  

```css
.container {
	place-content: space-between center;
}
```

-----

### 개별 아이템 세로 정렬  
해당 아이템을 세로(column축) 방향으로 정렬  
아이템에 적용  

align-self  

```css
.item {
	align-self: stretch;
	/* align-self: start; */
	/* align-self: center; */
	/* align-self: end; */
}
```

### 개별 아이템 가로 정렬  
해당 아이템을 가로(row축) 방향으로 정렬  
아이템에 적용  

justify-self  

```css
.item {
	justify-self: stretch;
	/* justify-self: start; */
	/* justify-self: center; */
	/* justify-self: end; */
}
```

### place-self
align-self와 justify-self를 같이 쓸 수 있는 단축 속성  
align-self, justify-self의 순서로 작성하고, 하나의 값만 쓰면 두 속성 모두에 적용  

```css
.item {
	place-self: start center;
}
```

-----

### 배치 순서
각 아이템들의 시각적 나열 순서를 결정하는 속성  
숫자값이 들어가며, 작은 숫자일 수록 먼저 배치  

order  

```css
.item:nth-child(1) { order: 3; } 
.item:nth-child(2) { order: 1; } 
.item:nth-child(3) { order: 2; } 
```

-----

### z-index
z-index로 Z축 정렬  
(position 에서의 z-index 와 같음)  

```css
.item:nth-child(5) {
	z-index: 1;
	transform: scale(2);
}
```

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

## Flex
Flexible Box, Flexbox  
(float 나 inline-block 등의 기존 방식보다 훨씬 강력하고 편리)  

-----

### Flex 구현
```html
<!-- div.container - Flex Container(플렉스 컨테이너) //-->
<div class="container">
	<!-- div.item - Flex Item(플렉스 아이템) // -->
	<div class="item">helloflex</div>
	<!-- div.item - Flex Item(플렉스 아이템) // -->
	<div class="item">abc</div>
	<!-- div.item - Flex Item(플렉스 아이템) // -->
	<div class="item">helloflex</div>
</div>
```

```css
.container {
	display: flex;
	/* display: inline-flex; */
}
```

Flex 아이템들은 가로 방향으로 배치되고,   
자신이 가진 내용물의 width 만큼만 차지 (inline 요소처럼 레이아웃 배치 됨)    
height는 컨테이너의 높이만큼 늘어남  

-----

### Flex 배치 방향 설정 
> flex-direction  
```css
.container {
	/* 가로(행) 배치 (기본값) */
	flex-direction: row;
	/* 세로(열) 배치 */
	/* flex-direction: column; */

	/* 가로(행) 반전(역순) 배치 (오른쪽 정렬) */
	/* flex-direction: row-reverse; */
	/* 세로(열) 반전(역순) 배치 */
	/* flex-direction: column-reverse; */
}
```

-----

### Flex 줄넘김 처리 설정 
> flex-wrap  
```css
.container {
	/* 줄바꿈을 하지 않습니다. 아이템들이 컨테이너 밖으로 나갈 수 있음 (기본값) */
	flex-wrap: nowrap;
	/* 줄바꿈을 합니다. */
	/* flex-wrap: wrap; */
	/* 줄바꿈을 하는데, 아이템을 역순으로 배치합니다. */ 
	/* flex-wrap: wrap-reverse; */
}
```

-----

### Flex 배치 방향, 줄넘김 처리 한번에 설정
> flex-direction, flex-wrap의 순으로 한 칸 공백을 넣어 작성  
```css
.container {
	flex-flow: row wrap;
	/* 아래의 두 줄을 줄여 쓴 것 */
	/* flex-direction: row; */
	/* flex-wrap: wrap; */
}
```

-----

### Flex 정렬
> justify : 메인축 방향으로 정렬   
> align : 수직축 방향으로 정렬  

메인축 방향 정렬 justify-content  
```css
.container {
	/* 아이템들을 시작점으로 정렬 (기본값) */
	justify-content: flex-start;
	/* 아이템들을 끝점으로 정렬 */
	/* justify-content: flex-end; */
	/* 아이템들을 가운데로 정렬 */
	/* justify-content: center; */
	/* 아이템들의 “사이(between)”에 균일한 간격을 만들어 줌 */
	/* justify-content: space-between; */
	/* 아이템들의 “둘레(around)”에 균일한 간격을 만들어 줌 */
	/* justify-content: space-around; */
	/* 아이템들의 사이와 양 끝에 균일한 간격을 만들어 줌 */
	/* justify-content: space-evenly; */
}
```

수직축 방향 정렬 align-items
```css
.container {
	/* 아이템들이 수직축 방향으로 끝까지 쭈욱 늘어남 (기본값) */
	align-items: stretch;
	/* 아이템들을 시작점으로 정렬(아이템들이 상단 기준 정렬, 내부 내용에 따른 높이) */
	/* align-items: flex-start; */
	/* 아이템들을 끝으로 정렬(아이템들이 하단 기준 정렬, 내부 내용에 따른 높이) */
	/* align-items: flex-end; */
	/* 아이템들을 가운데로 정렬 */
	/* align-items: center; */
	/* 아이템들을 텍스트 베이스라인 기준으로 정렬 */
	/* align-items: baseline; */
}
```

수평, 수직 모두 가운데 정렬
```css
justify-content: center;
align-item: center;
```

여러 행 정렬 align-content  
flex-wrap: wrap;이 설정된 상태에서, 아이템들의 행이 2줄 이상 되었을 때의 수직축 방향 정렬을 결정하는 속성
```css
.container {
	flex-wrap: wrap;
	align-content: stretch;
	/* align-content: flex-start; */
	/* align-content: flex-end; */
	/* align-content: center; */
	/* align-content: space-between; */
	/* align-content: space-around; */
	/* align-content: space-evenly; */
}
```

-----

### Flex 아이템에 적용하는 속성들
유연한 박스의 기본 영역 flex-basis  
```css
.item {
	flex-basis: auto; /* 기본값 */
	/* flex-basis: 0; */
	/* flex-basis: 50%; */
	/* flex-basis: 300px; */ /* width 가 300px 이 안되는 것은 300px로 늘어나고, 300px 이 넘는 것은 그대로 유지 */
	/* flex-basis: 10rem; */
	/* flex-basis: content; */
}
```

유연하게 늘리기 flex-grow  
flex-grow는 아이템이 flex-basis의 값보다 커질 수 있는지를 결정하는 속성  
flex-grow에는 숫자값이 들어가는데, 몇이든 일단 0보다 큰 값이 세팅이 되면 해당 아이템이 유연한(Flexible) 박스로 변하고 원래의 크기보다 커지며 빈 공간을 메우게 됨  
```css
.item {
	flex-grow: 1;
	/* flex-grow: 0; */ /* 기본값 */
}
```

유연하게 줄이기 flex-shrink  
flex-shrink는 flex-grow와 쌍을 이루는 속성으로, 아이템이 flex-basis의 값보다 작아질 수 있는지를 결정  
flex-shrink에는 숫자값이 들어가는데, 몇이든 일단 0보다 큰 값이 세팅이 되면 해당 아이템이 유연한(Flexible) 박스로 변하고 flex-basis보다 작아 짐   
```css
.item {
	flex-basis: 150px;
	flex-shrink: 1; /* 기본값 */
}
```

수직축으로 아이템 정렬 align-self  
align-items의 아이템 버전  
```css
.item {
	align-self: auto;
	/* align-self: stretch; */
	/* align-self: flex-start; */
	/* align-self: flex-end; */
	/* align-self: center; */
	/* align-self: baseline; */
}
```

배치 순서 order  
각 아이템들의 시각적 나열 순서를 결정하는 속성  
```css
.item:nth-child(1) { order: 3; } 
.item:nth-child(2) { order: 1; } 
.item:nth-child(3) { order: 2; } 
```

z-index  
Z축 정렬 (숫자가 클 수록 위로 올라옵니다.)
```css
.item:nth-child(2) {
	z-index: 1;
	transform: scale(2);
}
```

-----

### Flex flex-grow, flex-shrink, flex-basis 를 한 번에 쓸 수 있는 축약형 속성
```css
.item {
	flex: 1;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: 0%; */
	flex: 1 1 auto;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: auto; */
	flex: 1 500px;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: 500px; */
}
```

