# Poke Herb MSA 물류 서비스
전국에 있는 각 허브에서 도매업체로부터 주문을 받아 생산업체의 상품을 배송해주는 물류 서비스입니다.

## 💻 팀 구성
| 권민재 | 김예진 | 허진경 | 김남주 |
|:---:|:---:|:---:|:---:|
|[<img src="https://github.com/user-attachments/assets/eca6b310-b408-41e6-a5c0-0137df289a5d" width=130>](https://github.com/MJakeKwon)|[<img src="https://github.com/user-attachments/assets/c4cba737-23aa-4b75-985c-7d43f592d40c" width=130>](https://github.com/Yejin-source)|[<img src="https://github.com/user-attachments/assets/d1be4669-8e58-4c20-a615-6b6cc0835154" width=130>](https://github.com/jinnk0)|[<img src="https://github.com/user-attachments/assets/2c0a8519-b40c-4e67-b3a7-34dded204518" width=130>](https://github.com/RCNR)|
|주문, 배송|회원, 슬랙|허브, 허브 간 이동 정보|업체, 상품, 배송 담당자|

## MSA 서비스 구성
- [회원 서비스 (user-service)](https://github.com/PokeHerb/user-service)
- [허브 서비스 (hub-service)](https://github.com/PokeHerb/hub-service)
- [업체 서비스 (vendor-service)](https://github.com/PokeHerb/vendor-service)
- [상품 서비스 (product-service)](https://github.com/PokeHerb/product-service)
- [배송 담당자 서비스 (driver-service)](https://github.com/PokeHerb/driver-service)
- [주문 서비스 (order-service)](https://github.com/PokeHerb/order-service)
- [배송 서비스 (delivery-service)](https://github.com/PokeHerb/delivery-service)
- [슬랙 서비스 (slack-service)](https://github.com/PokeHerb/slack-service)

## Backend Technical Stack

본 프로젝트는 **마이크로서비스 아키텍처 (MSA)** 기반으로 설계되었으며, 높은 확장성, 안정성 및 관측 가능성(Observability)을 확보하기 위해 다음과 같은 기술 스택을 채택했습니다.

#### 1. Core Development & Runtime

| 기술  | 설명 |
| :--- | :--- |
| **Spring Boot** | **독립 실행형(Stand-alone)** 상용 수준의 Spring 기반 애플리케이션을 쉽게 생성하기 위한 프레임워크입니다. 마이크로서비스의 빠른 개발과 배포를 지원합니다. |


#### 2. Service Discovery & Connectivity

| 기술 | 설명 |
| :--- | :--- |
| **Eureka**| **서비스 디스커버리 서버** 역할을 수행합니다. 각 마이크로서비스 인스턴스가 자신의 위치를 등록하고, 다른 서비스들이 이 정보를 통해 서로 통신할 수 있도록 돕습니다. |


#### 3. Observability (Monitoring, Logging, Tracing)

시스템의 상태를 관측(Observability)하고 문제를 빠르게 진단하기 위한 핵심 도구들입니다. 

| 기술 | 설명 |
| :---  | :--- |
| **Prometheus** | 시계열 데이터(Metrics)를 수집하고 저장하는 시스템입니다. 서버, 애플리케이션 등에서 발생하는 성능 지표를 모니터링하는 데 사용됩니다. |
| **Grafana** | **시각화 툴**로, Prometheus 및 Loki 등 다양한 데이터 소스를 연결하여 **대시보드를 구축**하고 실시간 모니터링 환경을 제공합니다. |
| **Loki** | **로그 집계 시스템**으로, Prometheus와 유사한 라벨링 방식을 사용하여 로그를 저장하고 효율적으로 쿼리합니다. |
| **Zipkin**  | **분산 트레이싱(Distributed Tracing) 시스템**입니다. 마이크로서비스 환경에서 하나의 요청이 여러 서비스를 거쳐가는 과정을 추적하여 **성능 병목 지점**을 식별하는 데 사용됩니다. |


#### 4. Data & Messaging

| 기술 | 설명 |
| :---  | :--- |
| **PostgreSQL (Postgres)**  | 오픈소스 객체-관계형 데이터베이스(ORDBMS)입니다. 뛰어난 확장성, 안정성, 데이터 무결성을 제공하며 주 데이터 저장소로 사용됩니다. |
| **PgRouting** | PostgreSQL의 **PostGIS** 확장 기능을 활용하여 **지리 정보 시스템(GIS) 기반의 경로 탐색** 및 네트워크 분석 기능을 제공합니다. |
| **Redis** | **인메모리 데이터 구조 저장소**로, 주로 **고속 캐싱(Caching)**, 세션 관리, 순위표 등 빠른 읽기/쓰기가 필요한 곳에 사용됩니다. |
| **RabbitMQ** | **메시지 브로커** 역할을 수행합니다. 서비스 간의 **비동기 통신**을 구현하여 시스템의 결합도를 낮추고 안정적인 데이터 전송을 보장합니다. |


####  5. Security & Access Management

| 기술 | 설명 |
| :--- | :--- |
| **Keycloak**  | **ID 및 접근 관리(IAM) 솔루션**입니다. **OAuth 2.0 및 OpenID Connect**를 기반으로 **싱글 사인 온(SSO)**, 사용자 관리, 권한 부여 등을 중앙에서 처리하여 서비스의 보안을 강화합니다. |

## 시스템 아키텍처
<img width="1532" height="885" alt="image" src="https://github.com/user-attachments/assets/941be41a-0d19-4c13-9c6a-53b0f818374a" />

## ERD
<img width="1380" height="842" alt="image" src="https://github.com/user-attachments/assets/8456ccf0-45ee-4cb2-bf19-87cac1362f00" />

## 플로우 차트
<img width="1231" height="771" alt="image" src="https://github.com/user-attachments/assets/87f98e9f-0efb-4b86-9ceb-404b7a5da4ca" />

## 기술 명세서

