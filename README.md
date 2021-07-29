# 2021_summer_internship

:office: <a href='https://www.geoplan.kr/'>주식회사 GEOPLAN</a> <br>
:date: 기간 : 2021.07.01 ~ 2021.08.31 <br>
:hourglass_flowing_sand: AM 09:30 ~ PM 18:30 <br>
:pencil:배우고 있는것... Spring Framework, IoT, MariaDB, UI/UX  <br> <br>
#### 1일차
* 부서 배정/ 회사 소개 및 프로젝트 아이디어 소개
* Google Smart Home과 Assistant간의 관계 및 동작원리 파악 (<a href="https://medium.com/google-developers/jdanielmyers-smart-home-eac8f87fd56e">참고</a>)
* AoA(Angle of Arrival), RTLS(Real Time Location System) 기술 공부(<a href="https://searchmobilecomputing.techtarget.com/definition/real-time-location-system-RTLS#:~:text=A%20real%2Dtime%20location%20system%20(RTLS)%20is%20one%20of,manufacturing%20plant%20to%20a%20person.">참고</a>)
* Location device로 대체하여 구현할 수 있는 아이디어 생각
#### 2일차
* cloud computing study
* 집 외부에서 집 안의 cloud를 접근 가능하게 하려면 어떻게 해야할지 (고정ip만으로 될까?) 
* Smart Home Study
* 다음주 발표 PPT 만들기
#### 3일차
* 개발부장님 피드백
* Hole Punching 기술 공부 (<a href="https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=stallon72&logNo=10140690228">참고</a>)
* Smart Home Map 기능 구현 (Device안에 집 도면과 가구 위치 포함 + 사용자의 실시간 동선)
* 기존 음성 제어에서 위치 기반 자동화로 대체할 것인데 어떻게 구현하면 좋을지
* 내일 연구원님 UI/UX 계획 설명 
#### 4일차
* 연구원님 UI/UX 계획안 설명 및 피드백
* Webhook 기술 공부
* UWB, Beacon 개념 파악
* api 연동 개발 
#### 5일차
* SYNC, QUERY, EXECUTE, DISCONNECT intent 시 JSON 코드 분석
* Google API Search
* SmartThings 알아보기
#### 6일차
* SmartThings API 공부
#### 7일차
* 7일간 스터디 & 개발 내용 발표 및 피드백(부장님, 대표님, 개발팀장님)
* UI/UX 수정안 확인
* OAuth, SmartThings Rooms 봐보기
* API 연동 및 DB 
#### 8일차
* Google Open API 가져와 화면에 띄우기
* 데이터 DB 저장 및 연동
* Spring Server 개발에 앞서 기초적인 부분 다시 공부해오기
#### 9일차
*
#### 10일차
* Android UI 작업
* DB 설계
#### 11일차
* Android UI 작업
* MariDB 설치
#### 12일차
* Android UI 작업
* DB Table 설계 전 요구사항 분석
#### 13일차
* Database 테이블 설계
* DB 개념 공부하기

## 프로젝트 시작 

(배운내용/코드 교정받은 코드/내용 정리하기)

|Tool(IDE)|개발 내용|키워드|
|------|---|---|
|STS|Spring jdbc를 이용해서 mariaDB(HeidiSQL)값 JSon 형태로 불러오기|Spring STS gradle JDBC JSON|
|Android Studio|STS와 App 연동(계획)|.|
|MariaDB(HeidiSQL)|table설계(진행중)|프로젝트 요구사항|

#### ❤️피드백(DAO 코드, MariaDB 연결)

##### 1) DAO code

* 내 코드
  ```
  @Component
  public class UserDao {
	
	@Autowired
	private JdbcTemplate jdbcTemplate;
	
	public Map<String, Object> getName(int seq) throws Exception {
		String sql = "SELCET * FROM smart_home";
		return jdbcTemplate.queryForMap(sql);
	}
  }

  @Autowired
	  public void setDataSource(DataSource dataSource) {
	    this.jdbcTemplate = new JdbcTemplate(dataSource);
	  }
    ```
> JSON 형태로 결과 출력하기
  
  ![Inkedjson형식_LI](https://user-images.githubusercontent.com/52366841/127414929-273ee5e6-2510-47e3-acec-80419b5fc3e9.jpg)
  

* 어노테이션 @Autowired @Bean @Repository 검색해보기
* 오류해결?  DAO 불러오는 부분 UserDao userdao = new UserDao() x -> 전역변수로 빼고 @Autowired 어노테이션 추가 UserDao userdao; 으로 수정하니까 Bean 인젝션 잘 됨
  (<a href="https://namubada.net/98">참고</a>)

