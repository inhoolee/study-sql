# BigQuery

## OLAP (Online Analytical Processing)

OLTP 대신 분석을 위한 기능 제공

## BigQuery 소개

Google Cloud의 OLAP + Data Warehouse

## BigQuery 장점

- OLAP 도구로 속도가 빠름
- Firebase, Google Analytics4 데이터를 쉽게 추출 가능
- 데이터 웨어하우스를 사용하기 위해 서버(컴퓨터)를 띄울 필요 없음

## BigQuery 구성 요소

- 프로젝트
- 데이터셋
- 테이블

## 회사에 들어가서 선택한다면?

- 인력이 적고 구글 위주로 쓴다면 -> BigQuery
- AWS 클라우드 메인이라면 -> AWS RedShift
- 여러 클라우드를 함께 쓴다면 -> Snowflake
- AI, 딥러닝, 대규모 로그 분석도 필요하다면 -> Databricks

결국 비개발자와 함께 일한다면 계정 관리도 그렇고 GA와 연결도 생각하면 BigQuery를 쓰지 않을까?

## 공식문서

- [Bigquery 공식 문서](https://cloud.google.com/bigquery/docs?hl=ko)
- [Release note](https://cloud.google.com/bigquery/docs/release-notes)
  - slack feed 추가 (/feed subscribe https://cloud.google.com/feeds/bigquery-release-notes.xml)

## 스케줄 쿼리

- 지속적으로 쿼리를 실행해야 하는 경우
- 쿼리의 연산이 오래 걸려서 미리 BigQuery Table로 저장하고 싶은 경우
- BigQuery Data Transfer Service API 사용 허용
- 쿼리에서 CURRENT_DATE() 등을 사용할 경우 => 시간이 지나면서 점점 데이터 탐색
양이 많아질 수 있음(비용 부과)
- 디버깅 등이 불편하기 때문에 데이터 엔지니어링 조직이 있다면 Airflow 등을 사용하는
것으로 하고, 개발 조직이 아닌 경우에 스케줄 쿼리를 사용하기도 함
- 스케줄 쿼리 네이밍 규칙이 있으면 좋음. 마음대로 이름을 생성해서 추후에 관리가
어려워지는 경우도 존재함. 예 : {팀_이름}_{지표}_{수정일자}

## UDF (User Defined Function)

사용자가 정의한 함수

언제 사용하면 좋을까?

- 반복적으로 작업해야 하는 함수
- 팀 공용으로 사용해야 하는 전처리 규칙이 필요한 경우
- SQL로 실행하기 어려운 함수(자바스크립트로 UDF 만들 수 있음)

종류

- 임시(Temp) UDF : 쿼리문에서만 사용할 수 있는 UDF
- 영구(Persistent) UDF : 데이터셋에 저장되는 UDF

UDF를 만들 수 있는 언어

- SQL
- JavaScript : 속도 이슈가 존재할 수 있음. 약간의 개발 지식이 약간 필요
