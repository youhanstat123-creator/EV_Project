<div align="center">

# ⚡ EV_Project

> **번호판 인식 기반 전기차 충전구역 통합관리 시스템**
> Vue.js로 구현한 실시간 충전 모니터링 & 사용자/관리자 권한 분리 대시보드

![Vue.js](https://img.shields.io/badge/Vue.js-3.x-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7.x-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Axios](https://img.shields.io/badge/Axios-1.x-5A29E4?style=for-the-badge&logo=axios&logoColor=white)
![Chart.js](https://img.shields.io/badge/Chart.js-4.x-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)

</div>

---

## 🎯 What & Why

| | |
|---|---|
| **무엇을** | 전기차 충전구역의 실시간 상태를 번호판 인식으로 자동 식별하여 통합 관리하는 웹 시스템 |
| **왜 만들었나** | 전기차 보급 확대에 따른 충전구역 관리 부재 문제 해결 + 사용자/관리자 역할 분리로 실제 서비스 구조 구현 |
| **누구를 위해** | 충전구역 운영 관리자 & 전기차 사용자 |

---

## 🖥 실행 화면

| 사용자 대시보드 | 관리자 대시보드 |
|:---:|:---:|
| ![사용자](사용자%20대시보드.PNG) | ![관리자](관리자%20대시보드.PNG) |

---

## 🏗 Architecture

EV_Project/
├── frontend/ (Vue 3 SPA)
│   └── src/
│       ├── views/
│       │   ├── Login.vue / Signup.vue           # 인증
│       │   ├── EVUserDashboard.vue              # 사용자 대시보드
│       │   ├── EvChargingZoneMonitoring.vue     # 충전구역 실시간 모니터링
│       │   ├── EVVideoBoard.vue                 # 번호판 인식 CCTV
│       │   └── EvDatabaseUsage.vue              # DB 현황/통계
│       ├── components/ # 재사용 UI 컴포넌트
│       └── router/     # 권한별 라우팅
└── backend/ (Spring Boot REST API)

---

## 💡 Technical Highlights

### 1. 🔐 Role-Based UI Routing (사용자/관리자 권한 분리)
Vue Router의 beforeEach 가드를 활용해 로그인 사용자의 역할(User/Admin)에 따라 접근 가능한 화면을 분기 처리. 관리자 전용 메뉴는 일반 사용자에게 완전 비노출.

### 2. 📊 Chart.js 실시간 충전 현황 시각화
Chart.js를 Vue 컴포넌트에 통합하여 충전구역 현황(사용중/대기중/고장)을 도넛 차트로 시각화. axios의 async/await 패턴으로 API 응답 후 차트 데이터 반응형 업데이트 구현.

### 3. ⚡ 번호판 인식 API 연동
백엔드의 번호판 인식(OCR) 결과를 REST API로 수신, Vue 반응형 데이터(ref)에 즉시 반영하여 차량 입출차 상태를 실시간으로 UI에 업데이트.

---

## 🛠 Tech Stack

| 구분 | 기술 |
|------|------|
| **Frontend** | Vue 3, Vue Router 5, Vite 7 |
| **상태관리** | Composition API (ref, reactive) |
| **HTTP 통신** | Axios 1.x |
| **데이터 시각화** | Chart.js 4.x |
| **Backend** | Java, Spring Boot |

---

## 📊 Lessons Learned

**[이슈 1] API 비동기 처리** - axios 호출 후 차트가 빈 상태로 렌더링 → async/await + nextTick() 조합으로 해결

**[이슈 2] 권한별 UI 갱신** - 역할 전환 시 이전 메뉴 잔류 → 인증 상태를 watch로 메뉴 동기화 처리

---

## 🚀 Getting Started

cd frontend && npm install && npm run dev

---

## 👤 My Role — 프론트엔드 전체 단독 담당

- Vue 3 컴포넌트 구조 설계 및 전체 화면 구현
- Vue Router 사용자/관리자 권한별 라우팅 처리
- Axios API 연동 및 비동기 데이터 바인딩
- Chart.js 기반 충전 현황 시각화
- 반응형 UI 및 동적 화면 전환 구현
