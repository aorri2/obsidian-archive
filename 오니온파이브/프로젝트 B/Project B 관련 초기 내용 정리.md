- 프로젝트 B 관련 내용은 스페이스에서 확인해보면 됨

## 알아볼것들
- LANGCHAIN 알아보기
- LLM도 알아보기
- ChatGPT 유사도, VectorDatabase 등등 알아보기
- 

## 제품 소개
- 오큐파이는 상담원의 편의를 위해 문의를 한곳에 모으고 처리하는 서비스
	- 오큐파이는 고객 지원을 전화가 아닌 다양한 채널로 처리함에 가치를 둠
- 프로젝트 B는 AI라는 화두가 있어, 기업 가치를 높이기 위해 적용해보기 위한 취지를 가진 프로젝트
- Open API를 이용해, Q&A에 있는 내용을 고객 지원 영역에서 자동 답변으로 사용하려 함
	- 실제로 고객사 2곳 정도에서 사용 의향이 있음
- 팀장님 백엔드 프론트를 다 하기에는 벅차서, 프론트 작업 도움을 드릴 예정
- 예전에 이력서 ai로 면접 질문 뽑아주는 저장소 함 다시 보기
- IA 구조도 -> 메뉴 구조도
- sentry -> ai bot으로 한번 해보기
- 우리 서비스 같은 경우에는 oqupie 고객센터안에 추가 될 예정
- 대화형 프론트 시스템들 많이 참고해봐야 할듯
- DocsBot 시스템을 벤치마킹해서 만들 듯
- 오큐파이 톡플레이스의 꾸미기쪽 소스코드 있어서 참고해도 좋을 듯
- 실시간성 기능은 아니라 ㄹ소켓 통신은 안해도 됨
- 가입 페이지부터 만들듯
	- 시간 날 때 가입 페이지 로그인 페이지 함 만들어보기
- 공통 레이아웃 정의중인 단계임
- 100페이지면 사이즈 별로 분할함
- 분할한 스트링을 각각 DB에 저장함
	- 임베딩 : vector 형태의 무언가(?) LLM이 알아들을 수 있는 언어
- 질문할 때는, 유사도 검색을 함
	- 100페이지를 1000개 정도로 나눴을 때, 유사한 것들에 대해 찾아옴
- 유사도를 잘 찾는게 중요 할 듯
- 문서의 후보군을 추출해서 openAI한테 전달하는 것
- 프로젝트 관련 주요 사항들은 스페이스 에서 하기
	- 스페이스 댓글 통해서 일정 관련 내용 이야기 하면 됨
- 피그마 디자인을 리액트로 구현할 때, Untitled UI를 사용하고 계심
- ant design을 쓰면 html이나 css에 대해 깊이 관여 안해도 됨
	- ant design을 쓰면 새로운 툴에 대해 하나를 또 새로 배워야 된다라는 단점이 있음
	- 동시에 디자인과 개발이 가능해서 가능

- 내가 선택 가능한 방식은 ant design 방식과 tailwind css 방식이 있음
	- tailwind : 피그마 파일이 없음, 대표님은 언타이틀로 만들고 나는 tail wind로 만들게 됨
	- 기본적으로는 개발 속도가 가장 중요함
- 디자인 템플릿을 어떤걸로 같이 시작할 것인지 조사

- 정해진 레이아웃 영역에 반응형이 되어야함
![[Pasted image 20231113142334.png]]
- 위 레이아웃 참고해서, 레이아웃 구조 잡기
- **Postman으로 API 명세 진행 예정**
	- API 변동이 많아지거나 하면, swagger 고민중이심
	- 최대한 Restful로 API 구현 예정
- 

## TODO
- [x] tailwind VS AntDesign 📅 2023-11-13 ✅ 2023-11-13
	- 둘다 PoC한번 해보고 사용성 테스트 해보기
	- 유튜브 보고 둘다 한번 해보기
- 패키지 구조 잡기
- setup 툴로 npm,yarn,pnpm등 어떤거 쓸지 고민
- formatter, 컨벤션 등등 룰 어떻게 할지
- 기본 뼈대 대부분 잡아보기
- 상태 관리툴도 고민해보기
- 리액트 리마인드 해보기
- 프로젝트 B 쪽 Space - Develop 하위에 정리하기
- react 토큰 인증 연습