# GNB

___
___
## 기능 설명

- 상단 사용자 공통 메뉴 영역
- 주요 기능
  - [사용자 유형에 따른 메뉴 구성](#-가입자별-상품-정보-조회-기능)

___
## URL
- 콘솔 전체 페이지

___
## 관련 Source
- WebContent/d/consolemenu/topMenu.jsp
- WebContent/d/scripts/console.common.220_renewal.js
- WebContent/d/scripts/portal.common.cr.js
- WebContent/g/consolemenu/topMenu.jsp
- WebContent/g/scripts/console.common.220_renewal.js
- WebContent/g/scripts/portal.common.cr.js
- /src/ktcloudportal/epc/servlet/IsSvcSvrProcess.java

___
## 업무 flow
1. 로그인 여부 확인
2. 사용자 유형 확인<br>
: Root 사용자(그룹 Admin), Root 사용자(일반 사용자 : 그룹 사용자가 아니거나 그룹원인 경우), IAM 사용자<br>
3. 사용자 유형에 따른 메뉴 표시<br>
3-1. IAM 사용자<br>
: 알림, 사용자 계정, 로그 아웃 이외의 메뉴는 표시 안함<br>
: 정책상 개인 정보 영역은 접근 못함<br>
3-2. 그룹 Admin<br>
: 모든 메뉴 표시, 그룹내 그룹원 정보 표시함<br>
3-3. Group 원
: 모든 메뉴 표시, 그룹내 그룹원 정보 표시 안함<br>

___
## 주요 기능 상세

### 가입자별 상품 정보 조회 기능

### Database
- TBMB_GROUP
- TBMB_GROUP_USER


### API List
- IAM 사용자 판단:Session내 'iamid'로 판단
  - To Be에서 API화 필요<br><br>
- 그룹 user 조회 : getGroupUserSelect
  - 서블릿 : IsSvcSvrProcess
  - command : getGroupUserSelect
  - parameter : memsq
    - 그룹원 조회 결과 1명 이상인 경우 그룹 Admin으로 판단, 조회 결과가 없으면 일반 사용자<br>
	- To Be : 그룹원 조회 결과 첫번째는 Admin, 나머지는 그룹원 순으로 조회 되도록 개발(임창준과장 요청)<br>
  - 관련 쿼리 : IsSvcDao.getGroupUserSelect 참조
- 메뉴 표시
  - topMenu.jsp, console.common.220_renewal.js에 
	- To Be : 메뉴 조회 API 개발 및 해당 API에서 처리<br><br>
___
### 참고 사항
- IAM : IAM 메뉴 참고
- Group : User > Group
- 상품 청약 : User > 결제 정보, All Service 참고
