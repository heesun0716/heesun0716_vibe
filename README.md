# 🌸 Premium MBTI Diagnosis Test 🌸

<div align="center">
  <img src="https://img.shields.io/badge/Language-HTML5%20%2F%20CSS3-FFB6C1?style=flat-square&logo=html5&logoColor=white"/>
  <img src="https://img.shields.io/badge/JavaScript-Vanilla%20JS-FFC0CB?style=flat-square&logo=javascript&logoColor=white"/>
  <img src="https://img.shields.io/badge/Design-Glassmorphism-FF69B4?style=flat-square"/>
  <img src="https://img.shields.io/badge/Build-Success-pink?style=flat-square&logo=github"/>
</div>

<br/>

> 💡 **"단 3분 만에 마주하는 진짜 나의 모습"**
> 본 프로젝트는 사용자의 일상적인 행동 패턴을 기반으로 성격 유형(MBTI)과 심리적 마인드셋을 다각도로 분석하여 프리미엄 대시보드 리포트를 제공하는 **고급형 성격유형 진단 웹 애플리케이션**입니다.

---

## 💕 주요 UI/UX 기능 (Premium Features)

감각적인 핑크빛 그라데이션 오라와 모던한 컴포넌트로 사용자 경험(UX)을 극대화했습니다.

* ✨ **글래스모피즘 메인 카드**: 반투명 레이어와 블러 효과를 극대화한 미려한 UI 카드 디자인
* 🎨 **다이내믹 백그라운드**: 백그라운드에서 부드럽게 움직이며 펄싱(Pulse)하는 프리미엄 그라데이션 오브(Orb) 이펙트
* 🌓 **테마 스위처 (다크 모드)**: 눈이 편안한 다크 테마와 세련된 라이트 테마 간 실시간 CSS 토글 전환 기능
* 🎵 **사운드 및 인터랙션**: 정밀한 웹 오디오 컨트롤 사운드 활성화/비활성화 스위치 내장
* 📊 **실시간 애니메이션**: 다이내믹 진행도 바(Progress Bar), 페이드 트랜지션, 로딩 페이지 엔진 구동

---

## 🔮 시스템 아키텍처 및 로직 설명 (Technical Logic)

웹 프론트엔드의 최신 기술 트렌드를 반영하여 외부 무거운 라이브러리 없이 순수 Vanilla 기술로만 가볍고 빠르게 빌드되었습니다.

### 1️⃣ 컴포넌트 기반 데이터 핸들링
* **12문항 정밀 프로파일링 시스템**: 사용자의 성향을 완벽하게 필터링할 수 있는 엄선된 12가지 커스텀 핵심 문항 기반 설계
* **동적 돔(DOM) 조작**: 질문 및 답변 선택지 선택 시 데이터 흐름에 맞춰 실시간으로 구조가 변경 및 생성되는 Dynamic UI 렌더링 시스템

### 2️⃣ 4차원 성향 밸런싱 연산 알고리즘
사용자의 응답 스코어에 따라 MBTI의 4대 핵심 축을 실시간 수치화하여 계산합니다.
$$\text{Extraversion (E)} \iff \text{Introversion (I)}$$
$$\text{Sensing (S)} \iff \text{Intuition (N)}$$
$$\text{Thinking (T)} \iff \text{Feeling (F)}$$
$$\text{Judging (J)} \iff \text{Perception (P)}$$
* 연산 완료 후 **좌/우 우세 성향**에 따라 게이지 바의 색상과 방향이 CSS 변수(`--accent-gradient`)를 통해 실시간 반전 처리됩니다.

### 3️⃣ 연산 지연 가상화 (Loading Page Layer)
* 유저가 모든 응답을 마치면 즉시 결과로 넘어가지 않고, 가상 데이터 연산 레이어가 작동하여 프리미엄 리포트를 정밀 생성하는 듯한 몰입도 높은 UX 흐름을 구현했습니다.

---

## 🛠️ 개발 기술 스택 (Tech Stack)

<table align="center">
  <tr>
    <td align="center" width="160px">
      <img src="https://img.shields.io/badge/HTML5-FFB6C1?style=for-the-badge&logo=html5&logoColor=white"/>
    </td>
    <td align="center" width="160px">
      <img src="https://img.shields.io/badge/CSS3-FFC0CB?style=for-the-badge&logo=css3&logoColor=white"/>
    </td>
    <td align="center" width="160px">
      <img src="https://img.shields.io/badge/JavaScript-FF69B4?style=for-the-badge&logo=javascript&logoColor=white"/>
    </td>
  </tr>
</table>

* **Font**: 리드미컬하고 높은 가독성을 확보하기 위해 프리미엄 웹 폰트인 `Pretendard (v1.3.9)` 환경 적용
* **Responsive**: 모바일 환경 최적화를 위한 미디어 쿼리(`@media`) 세부 브레이크 포인트 디바이스 맞춤 설계

---

## 🚀 실행 및 테스트 방법 (How to Run)

본 프로젝트는 순수 웹 표준 기술로 작성되어 별도의 빌드 과정이나 서버 오픈 없이 즉시 테스트가 가능합니다.

```bash
# 1. 원격 저장소의 코드 클론 받기
git clone [https://github.com/your-username/premium-mbti-test.git](https://github.com/your-username/premium-mbti-test.git)

# 2. 프로젝트 디렉터리로 이동
cd premium-mbti-test

# 3. index.html 파일을 브라우저로 더블 클릭하거나 로컬 서버로 실행
# (VS Code 사용자라면 Live Server 익스텐션 실행을 추천합니다! 🌸)
