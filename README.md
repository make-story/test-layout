# HTML Layout TEST   

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

- 그리드 컨테이너 (Grid Container)
display: grid를 적용하는, Grid의 전체 영역입니다. Grid 컨테이너 안의 요소들이 Grid 규칙의 영향을 받아 정렬된다고 생각하면 됩니다. 위 코드 <div class=”container”></div>가 Grid 컨테이너에요.

- 그리드 아이템 (Grid Item)
Grid 컨테이너의 자식 요소들입니다. 바로 이 아이템들이 Grid 규칙에 의해 배치되는 거에요. 위 코드에서 <div class=”item”></div>들이 Grid 아이템입니다.

- 그리드 트랙 (Grid Track)
Grid의 행(Row) 또는 열(Column)

- 그리드 셀 (Grid Cell)
Grid의 한 칸을 가리키는 말이에요. <div>같은 실제 html 요소는 그리드 아이템이고, 이런 Grid 아이템 하나가 들어가는 “가상의 칸(틀)”이라고 생각하면 됩니다.

- 그리드 라인(Grid Line)
Grid 셀을 구분하는 선입니다.

- 그리드 번호(Grid Number)
Grid 라인의 각 번호입니다.

- 그리드 갭(Grid Gap)
Grid 셀 사이의 간격입니다.

- 그리드 영역(Grid Area)
Grid 라인으로 둘러싸인 사각형 영역으로, 그리드 셀의 집합이에요.

```css
.container {
	display: grid;
	/* display: inline-grid; */ /* block과 inline-block의 관계와 비슷 */
}
```
