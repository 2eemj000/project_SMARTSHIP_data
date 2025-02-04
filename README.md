
## 💡 SmartShip
[K-Digital 부산대 24-7회차] AI 활용 빅데이터분석 풀스택웹서비스 SW 개발자 양성과정 AI 학습모델 웹서비스 개발 프로젝트

- **주제:** 선박, 육상, 공급업체간 기부속/선용품 공급망 관리 시스템
- **목표:** 선박-해운선사-공급업체의 ROLE별 프로세스를 구축하여 기부속 및 선용품의 판매, 주문, 공급 과정 관리.
  
&nbsp;

## 📈 개발 기간
> 2024.08.26 - 2024.10.02.
&nbsp;

## 🔧 개발 환경
> `언어 및 프레임워크:` Java 17.0.10, React 18.2.0, Spring Boot 2  
> `IDE:` STS4  
> `DB:` MySQL 8.0.37  
> `머신러닝/ 딥러닝:` BERT, BertTransformer, XGBClassifier, LightGBMregressor

<!-- 여기에 공백을 추가합니다 -->
&nbsp;

  
## 📋 웹 서비스 주요 기능 요약
### 공통 기능
- **로그인**: 사용자 인증 및 JWT 발급
- **회원가입/탈퇴**: 사용자 정보 등록 및 계정 비활성화

### 선박
- **물품리스트**: 카테고리별 물품 조회
- **장바구니**: 물품 추가, 수량 조정 및 물품 삭제
- **주문내역**: 주문 내역 조회
  
### 해운선사(육상)
- **일정관리**: 발주 일정 계산 및 관리.
- **구매요청**: 리드타임 기반으로 최적의 발주 날짜에 물품 발주
- **발주관리**: 발주 상태(발주예정 OR 발주 진행 중 OR 발주 완료) 업데이트 및 관리

### 공급업체(판매자)
- **물품 관리**: 업체별 판매하는 물품 등록, 수정, 삭제
- **공지사항**: 공급업체 관련 공지 조회
- **대시보드**: 실시간 물품 발주 내역 및 내 판매 현황 조회

### 관리자
- **공지사항 관리**: 공지사항 CRUD 처리
- **회원관리**: 회원 정보 조회 및 관리

<!-- 여기에 공백을 추가합니다 -->
&nbsp;

## 📌 모델 사용 주요 기능
### 공급업체의 새 상품 등록 시 카테고리 분류 추천
- **모델:** BERT 임베딩, BertTransformer, XGBClassifier
- **기능:** 사용자가 입력한 선용품 정보를 바탕으로 카테고리1, 2 분류.
- **성과 목표:** F1 스코어 85% 이상 달성.

### 해운선사 주문 시 리드타임에 따른 발주 날짜 추천
- **모델:** Word2Vec 임베딩, LightGBMregressor
- **기능:** 예상 리드타임을 바탕으로 품목별 리드타임과 최적의 발주 날짜를 추천.
- **성과 목표:** RMSE 및 MAE 10 이하.

<!-- 여기에 공백을 추가합니다 -->
&nbsp;

## 📊 데이터 분석
### 모델 선택 및 학습
- **카테고리 분류:** BERT 임베딩과 BertTransformer를 사용하여 'Machinery, Assembly, 청구품목, Part No.1' 결합하여 텍스트 임베딩 생성.
- **리드타임 예측:** 텍스트는 Word2Vec 임베딩, 수치형 피쳐는 리드타임 및 창고입고일 기반 환율 등 추가 피처 생성하여 사용.
- **성능 평가 및 튜닝:** K-폴드 교차 검증, 하이퍼파라미터 조정, Dropout, L2 정규화.

[데이터 분석 KPI 회고록 노션 페이지](https://www.notion.so/f881a47083ea4b4295ce94f2be6a3920)

<!-- 여기에 공백을 추가합니다 -->
&nbsp;

 
|Home|(선박)구매요청|(해운선사)대시보드|(해운선사)요청건별 품목 및 리드타임 확인-Model1|
|---|---|---|---|
|![로그인](https://github.com/user-attachments/assets/7e08dd1d-02d2-42ba-92b7-5e58028ef9ba)|![구매요청내역](https://github.com/user-attachments/assets/4409c019-2d13-4aba-8f91-ab03d3913868)|![해운선사대시보드+리드타임](https://github.com/user-attachments/assets/5de51580-b91c-459c-a8f8-c6bc43b828a1)|![발주목록확인+리드타임확인](https://github.com/user-attachments/assets/49229cf7-4cb4-446d-83f9-131d2eee12ec)|
|선박/해운선사/공급업체 Role 별 회원가입 및 로그인 |선박은 창고출고일 지정 후 선사에 구매요청| 발주요청 품목 리스트 / 출고일정 / 리드타임 확인 가능|요청 건별 목록 조회|

|(해운선사)대체상품 확인 |(해운선사)품목의 과거 리드타임 확인 |(공급업체)대시보드|(공급업체)기자재 등록-Model2|
|---|---|---|---| 
|![대체상품확인](https://github.com/user-attachments/assets/99bf4390-e584-4502-8d21-8c8dd4601ad9)|![품목별 과거리드타임확인](https://github.com/user-attachments/assets/62a2a0b7-f608-4c2e-8c55-73b0a2b086be)|![공급업체자기물건확인](https://github.com/user-attachments/assets/eeaffd17-445b-4a57-8798-cd2ac655d3fb)|![기자재 등록](https://github.com/user-attachments/assets/138ce76c-397f-4d4c-9c85-9738280ed41c)|
|리드타임 over로 인하여 지정창고입고일에 입고가 불가능한 경우 alert=> 대체상품 추천|품목별 과거 리드타임 차트|공급업체로 들어온 주문 관리 및 조회|새로운 기자재 등록 시 카테고리 추천 분류|

<!-- 여기에 공백을 추가합니다 -->
&nbsp;
[![Watch the video](https://github.com/user-attachments/assets/37ef937e-c45e-415d-8793-32359c2f86ed)](https://www.youtube.com/watch?v=drF5rMgZzB0)
SMARTSHIP 시연 영상입니다.


