###Controller
```
@Controller
public class SampleController{
	//로그 객체 생성
	private static final Logger logger = LoggerFactory.getLogger(SampleController.class);
    
    @RequestMapping("sample/doA")
    //리턴 타입 없이 void일 경우, mapping된 url pattern이름과 동일한 jsp로 포워드한다.
    public String doA(Model model){
    	logger.info("doA called...");	//로그 출력
    	//model.addAttribute(key, value);
    	//map과 같이 key, value구조로 되어있다.
    	model.addAttribute("message", "welcome to Hompage");
    	//리턴 타입이 void면, 메서드가 종료된 후 doA.jsp로 포워드
    	return "sample/doB";	//doB.jsp로 포워드
    }
    
    @RequestMapping("sample/doB")
    public void doB(){
    	logger.info("doB called...");
        // 메서드가 종료된 후에 doB.jsp로 포워드
    }
    
    // ModelAndView : Model-데이터저장소, View-화면
    // 데이터와 포워드할 페이지의 정보
    // forward: 주소변경X, 화면전환, 대량의 데이터 전달
    // redirect: 주소변경O, 화면전환, 소량의 데이터 전달(get방식만 가능)
    @RequestMapping("sample/doC")
    public ModelAndView doC(){
    	logger.info("doC called...");
        //메서드가 종료된 후에 doC.jsp로 포워드
        //맴에 객체 저장
        Map<String, Object> map = new HashMap<String, Object>();
        map.put("product", new ProductVO("연필", 1000));
        // new ModelAndView("view의 이름", "map 변수명", 맵);
        return new ModelAndView("sample/doC", "map", map);
    }
    
    @RequestMapping("sample/doD")
    public String doD(){
    	//redirect인 경우, return type을 String으로 설정
        //doE.jsp로 리다이렉트
        return "redirect:/sample/doE";
    }
    
    @RequestMapping("sample/doE")
    public void doE(){
    	//doE.jsp로 포워드
    }
    
}
```

###View
####home.jsp
```
...
<title>컨트롤러 호출 연습페이지</title>
<script src="http:s//ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<%
	// 컨텍스트 메서드 호출
    String path = request.getContextPath();
/%>
<script>
	//json의 형식
    //{변수명: 값, 변수명: 값}
    //{name: "냉장고", price: 1000000}
    function doE(){
    	$.ajax({
        	type: "post",
            url: "<%=path%>/sample/doF",
            success: function(result){
            	console.log(result);
                $("#result").html("상품명 : "+result.productName+", 가격 : "+result.productPrice);
            }
        });
    }
</script>
<body>
	<h2>컨트롤러 호출 연습 페이지</h2>
    <a href="<%=path%>/sample/doA">doA</a> : model <br>
    <a href="<%=path%>/sample/doB">doB</a> : 단순호출 <br>
    <a href="<%=path%>/sample/doC">doC</a> : modelAndView <br>
    <a href="<%=path%>/sample/doD">doD</a> : redirect <br>
    <a href="javascript:doF()">doF</a> : json <br>
    <!-- 함수 호출 결과물 출력 -->
    <div id="result"></div>
</body>
```