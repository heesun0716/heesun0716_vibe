바이브 코딩 연습
# 🧬 정밀 성격유형 진단 테스트 (Premium MBTI)

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=ec4899&height=200&section=header&text=My%20UI%20Design%20System&fontSize=40&fontColor=ffffff" width="100%" />
</div>

> **유희선님의 성격 유형과 매칭된 최적의 UI 디자인 시스템 명세서 및 MBTI 테스트 웹 애플리케이션 리포지토리입니다.**

<br />

## 🌟 프로젝트 소개
- **프로젝트 명**: 정밀 성격유형 진단 테스트 (Premium MBTI)
- **배포 주소**: 🔗 [나의 MBTI 테스트 웹사이트](https://heesun0716.github.io/heesun0716_vibe/)
- **핵심 목표**: 사용자의 답변을 정밀하게 분석하여 16가지 성격 유형(MBTI)을 진단하고, 트렌디하고 세련된 UI/UX 환경을 제공합니다.

<br />

## 🎨 최종 선택된 UI 디자인 시스템 (Vibrant Pink)

작성자의 성격 성향을 기반으로 도출된 고유의 디자인 가이드라인입니다.

### 1. 시각 언어 및 컬러 시스템 (Color & Typography)
| 대분류 | 세부 가이드라인 항목 | 디자인 특징 및 수치 |
| :--- | :--- | :--- |
| **Vibrant Pink<br>컬러 시스템** | 핵심 팔레트 | <ul><li>`Primary`: #ec4899 (핑크)</li><li>`Secondary`: #db2777 (진한 핑크)</li><li>`Accent`: #f472b6 (밝은 핑크)</li></ul> |
| | 상태 알림 컬러 | <ul><li>`Success`: #10b981</li><li>`Warning`: #f59e0b</li><li>`Error`: #ef4444</li></ul> |
| | 배경 및 텍스트 | <ul><li>`Gray-50`: #fdf2f8 (화사한 배경)</li><li>`Gray-900`: #831843 (가독성 높은 텍스트)</li></ul> |
| **Corporate<br>폰트 시스템** | 타이포그래피 | <ul><li>`영문`: Roboto (300-700)</li><li>`한글`: 본고딕 (Noto Sans KR 300-700)</li><li>`크기 / 행간`: 16px 기준, 1.2 배율 / 1.4-1.5</li><li>`특징`: 전문적이고 신뢰감 있는 룩앤필 제공</li></ul> |

<br />

### 2. 레이아웃 및 컴포넌트 구조 (Layout & Structure)
* **블로그/아티클 레이아웃**: 중앙 컨테이너 가로폭을 `max-width: 768px`로 제한하여 타이포그래피 가독성을 최적화하고, 하단에 댓글창을 배치합니다.
* **Bootstrap Style 그리드**: 가장 표준화된 빠른 개발을 위해 `12컬럼` 구조를 채택하며, 간격은 `30px(1.875rem)`로 균일하게 설정합니다.
  * *Breakpoints*: sm(576px), md(768px), lg(992px), xl(1200px)
* **Luxury 공간 설계**: 프리미엄하고 넓은 공간감을 주기 위해 섹션 간격 `64px`, 페이지 여백 `80px`로 여유롭게 설계합니다.
* **Sharp Modern 컴포넌트**: 모서리 곡률을 주지 않는 `border-radius: 0px`와 입체감 있는 그림자(`box-shadow`) 조합으로 기술적이고 전문적인 느낌을 극대화합니다.

<br />

### 3. 인터랙션 및 성능 최적화 (Interaction & Performance)
```css
/* Scale Transform 인터랙션 효과 */
.component-btn {
    transition: transform 0.15s ease-out;
}
.component-btn:hover {
    transform: scale(1.02); /* 호버 시 미세한 확대 피드백 */
}
.component-btn:active {
    transform: scale(0.98); /* 클릭 시 눌리는 시각적 효과 */
}
