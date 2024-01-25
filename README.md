
![7](https://github.com/dino-21/0126/assets/80396471/39c9eed6-bdbf-473b-a780-b3bd57a97321)
![8](https://github.com/dino-21/0126/assets/80396471/3c16f36d-f33f-4de4-9c0c-39efd0d62c24)
![9](https://github.com/dino-21/0126/assets/80396471/a298db2f-3d8f-4324-9973-e5f0d3f8242e)


1. order by 보다는 인덱스

2. PK_BOARD라는 인덱스
인덱스와 오라클 힌트(hint)

3. ROWNUM 과 인라인 뷰

4. 오라클에서 페이지별 데이터 가져오는 거 확인


5. MyBatis와 스프링에서 페이징 처리
Criteria.java  검색기준
private int pageNum;    // 페이지 번호
private int amount;      // 페이지당 보여줄 개수

6. getListWithpaging() 메서드 작성 – Criteria타입을 파라미터로 사용함
public List<BoardVO> getListWithPaging(Criteria cri);


7. BoardMapper.xml 에 코드 추가

8. BoardMapperTests.java  페이징 테스트와 수정

9. BoardMapper.xml 에 코드 추가 수정

10. BoardMapperTests.java  코드 수정 후 테스트
Criteria cri = new Criteria(2,5);

11. BoardController과 BoardService 수정

12. BoardServiceTests.java 수정


13.   BoardController.java 코드 수정
List<BoardVO> list = boardservice.getList(cri);


14.  BoardControllerTests.java 목업 가짜서버에서 테스트 (위와 동일한 결과 확인) 

 포스트맨에서 확인BoardControllerTests.java코드에서 우클릭
Run As > JUnit Test

--
15. 페이징 화면 처리 
페이징의 끝 번호(endPage) 계산

페이징의 시작 번호(endPage) 계산

total을 통한 endPage의 계산








16. PageDTO.java   페이징 처리를 위한 클래스 설계

17. BoardController.java 코드 수정

18. list.jsp  JSP에서 페이지 번호 출력

19. list.jsp 페이지 번호 이벤트 처리 코드 수정

20. 실제 페이지 동작을 하는 부분은 별도의 <form> 태그를 이용해서 처리하도록 한다.  EL로 처리

21 <a> 태그가 동작을 못하도록 Javascript 처리를 한다.  js코드 추가

22 acitonForm 자체를 submit() 시킴

23  조회 페이지로 이동
<td>
    <a class="move" href='${board.bno}'>
    ${board.title}</a>
</td>


24. list.jsp 게시물 조회를 위한 이벤트 처리 추가     js 코드 추가

25. 조회 페이지에서 다시 목록 페이지로 이동 – 페이지 번호 유지

get.jsp 코드 추가
<form> 태그 추가

26.  수정 처리  pageNum과 amount 값이 존재하므로 <form>태그내에서 같이 전송할 수 있게 수정해야 함

27. 삭제 처리  pageNum과 amount 값이 존재하므로 <form>태그내에서 같이 전송할 수 있게 수정해야 함

28. 수정/삭제 페이지에서 목록 페이지로 이동

29. MyBatis에서 전체 데이터의 개수 처리

BoardMapper.java
BoardMapper.xml
BoardService.java
BoardServiceImpl.java
BoardController.java

list.jsp 수정

30. 톰캣 서버에서 확인 prev, next버튼 클릭되는지 확인  
