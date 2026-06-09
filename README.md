<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>정밀 성격유형 진단 테스트 (Premium MBTI)</title>
    <style>
        /* Pretendard 및 Google Fonts Roboto 프리미엄 폰트 조합 */
        @import url("https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css");
        @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap");

        :root {
            /* 💗 Vibrant Pink 컬러 시스템 완벽 적용 */
            --primary: #ec4899;           /* 메인 핑크 */
            --primary-dark: #db2777;      /* 진한 핑크 */
            --primary-light: #fdf2f8;     /* Gray-50 대용 화사한 연핑크 */
            --accent: #f472b6;            /* 밝은 핑크 */
            --accent-gradient: linear-gradient(135deg, #ec4899 0%, #db2777 100%);
            --glow-color: rgba(236, 72, 153, 0.25);

            /* 시스템 알림 상태 컬러 */
            --success: #10b981;
            --warning: #f59e0b;
            --error: #ef4444;

            /* 라이트 모드 컬러 세팅 (Gray-50 베이스) */
            --bg-app: #fdf2f8;
            --card-bg: #ffffff;
            --border-color: rgba(131, 24, 67, 0.12);
            --text-main: #831843;         /* Gray-900 딥핑크 블랙 */
            --text-muted: #db2777;        /* 보조 텍스트 진한 핑크 */
            --option-bg: #ffffff;
            --option-border: #f472b6;
            --option-hover-bg: #fdf2f8;
            --progress-bg: #fdf2f8;
            --progress-bg-secondary: #f472b6;
            --badge-bg: #fdf2f8;
            --badge-text: #ec4899;
            --card-shadow: 0 2px 4px rgba(131, 24, 67, 0.15); /* Sharp Modern 공식 그림자 */
            --modal-bg: rgba(255, 255, 255, 0.98);
        }

        /* 다크 모드 변수 재정의 (럭셔리 다크 핑크 모드) */
        body.dark-theme {
            --bg-app: #4c0519;            /* 매우 깊은 초콜릿 핑크 블랙 */
            --card-bg: #831843;            /* Gray-900 메인 카드화 */
            --border-color: rgba(255, 255, 255, 0.15);
            --text-main: #fdf2f8;         /* 라이트 텍스트 체인지 */
            --text-muted: #f472b6;
            --option-bg: rgba(131, 24, 67, 0.6);
            --option-border: rgba(244, 114, 182, 0.3);
            --option-hover-bg: #db2777;
            --progress-bg: #4c0519;
            --progress-bg-secondary: #db2777;
            --badge-bg: #4c0519;
            --badge-text: #f472b6;
            --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.5);
            --modal-bg: rgba(131, 24, 67, 0.98);
        }

        * {
            box-sizing: border-box;
            /* 폰트 시스템: 영문 Roboto, 한글 본고딕/Pretendard 호환 설정 */
            font-family: 'Roboto', 'Pretendard', -apple-system, sans-serif;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-app);
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            /* Luxury 공간 설계: 기본 페이지 스페이싱 적용 */
            padding: 80px 24px; 
            transition: background-color 0.4s ease, color 0.4s ease;
            position: relative;
            overflow-x: hidden;
            font-size: 16px;
            line-height: 1.5; /* 행간 최적화 */
        }

        /* 프리미엄 핑크 은은한 배경 오버레이 */
        .glow-orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(140px);
            opacity: 0.15;
            z-index: -1;
            pointer-events: none;
        }
        .orb-1 {
            width: 500px;
            height: 500px;
            background: var(--primary);
            top: -150px;
            left: -150px;
        }
        .orb-2 {
            width: 600px;
            height: 600px;
            background: var(--primary-dark);
            bottom: -200px;
            right: -150px;
        }

        /* 아티클 맥스 가로폭 분배 + Sharp Modern (모서리 각진 0px) 컨테이너 설정 */
        .app-container {
            background: var(--card-bg);
            border: 2px solid var(--primary);
            border-radius: 0px !important; /* ⭐ Sharp Modern 컴포넌트: 모서리 각지게 */
            /* Luxury 공간 설계: 내부 컴포넌트 스페이싱 */
            padding: 48px;
            box-shadow: var(--card-shadow) !important; /* Sharp Modern 그림자 적용 */
            width: 100%;
            max-width: 768px; /* 블로그/아티클 중앙 가로폭 표준 준수 */
            transition: all 0.15s ease-out; /* Scale Transform 트랜지션 지속시간 맞춤 */
            position: relative;
        }

        /* 상단 네비게이션 헤더 바 */
        .header-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 32px; /* 컴포넌트 간격 고정 */
        }
        
        .theme-toggle, .sound-toggle {
            background: var(--badge-bg);
            border: 1px solid var(--primary);
            border-radius: 0px; /* Sharp Modern */
            width: 44px;
            height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: transform 0.15s ease-out;
            color: var(--text-main);
        }
        .theme-toggle:hover, .sound-toggle:hover {
            transform: scale(1.05);
            background: var(--option-hover-bg);
        }
        .header-controls {
            display: flex;
            gap: 12px;
        }

        /* 메인 액션 버튼 - Sharp Modern 스타일 */
        .btn-main {
            background: var(--accent-gradient);
            color: white;
            border: none;
            padding: 18px 36px;
            font-size: 1.15rem;
            border-radius: 0px; /* Sharp Modern */
            cursor: pointer;
            font-weight: 700;
            width: 100%;
            /* Scale Transform 인터랙션 완벽 적용 */
            transition: transform 0.15s ease-out; 
            box-shadow: 0 2px 4px rgba(0,0,0,0.15);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        .btn-main:hover {
            transform: scale(1.02) translateY(-2px); /* 인터랙션 규칙 */
            filter: brightness(1.05);
        }
        .btn-main:active {
            transform: scale(0.98);
        }

        /* 진행도 컴포넌트 */
        .progress-wrapper {
            margin-bottom: 32px; /* Luxury 스페이싱 */
        }
        .progress-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }
        .progress-text {
            font-size: 0.95rem;
            color: var(--text-muted);
            font-weight: 700;
        }
        .progress-percent-bubble {
            background: var(--primary);
            color: white;
            padding: 4px 10px;
            border-radius: 0px; /* Sharp Modern */
            font-size: 0.8rem;
            font-weight: 700;
        }
        .progress-bg {
            width: 100%;
            background-color: var(--progress-bg);
            height: 12px;
            border-radius: 0px;
            overflow: hidden;
            border: 1px solid var(--primary);
        }
        .progress-fill {
            width: 0%;
            height: 100%;
            background: var(--accent-gradient);
            transition: width 0.3s ease;
        }

        /* 뒤로가기 버튼 */
        .btn-back {
            background: none;
            border: 1px solid var(--primary);
            color: var(--text-muted);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 0.95rem;
            font-weight: 700;
            padding: 8px 16px;
            border-radius: 0px; /* Sharp Modern */
            transition: all 0.15s ease-out;
            visibility: hidden;
        }
        .btn-back:hover {
            color: var(--text-main);
            background: var(--option-hover-bg);
            transform: scale(1.02);
        }

        /* 페이지 전환 효과 */
        .page {
            display: none;
            animation: fadeIn 0.4s ease-out forwards;
        }
        .active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* 질문 헤더 */
        .question-title {
            font-size: 1.45rem;
            font-weight: 700;
            line-height: 1.5;
            margin-bottom: 32px; /* Luxury 컴포넌트 간격 */
            word-break: keep-all;
            text-align: center;
            color: var(--text-main);
            min-height: 60px;
        }

        /* 대답 선택지 버튼 - Sharp Modern 완벽 구현 */
        .opt-btn {
            background: var(--option-bg);
            border: 2px solid var(--option-border);
            color: var(--text-main);
            padding: 20px 24px;
            font-size: 1.05rem;
            border-radius: 0px; /* ⭐ border-radius 0px 절대 사수 */
            cursor: pointer;
            width: 100%;
            margin-bottom: 16px;
            text-align: left;
            transition: transform 0.15s ease-out, background-color 0.15s ease; /* Scale Transform */
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 16px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        .opt-btn:hover {
            border-color: var(--primary-dark);
            background-color: var(--option-hover-bg);
            transform: scale(1.015) translateY(-2px); /* 인터랙션 최적화 */
            box-shadow: var(--card-shadow);
        }
        .opt-btn:active {
            transform: scale(0.99);
        }
        .opt-badge {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 30px;
            height: 30px;
            border-radius: 0px; /* Sharp Modern */
            background: var(--primary);
            color: white;
            font-weight: 700;
            font-size: 0.9rem;
            flex-shrink: 0;
        }

        /* 인포 스펙 카드 데코레이션 */
        .start-badge {
            display: inline-flex;
            background: var(--primary-dark);
            color: white;
            padding: 6px 14px;
            border-radius: 0px;
            font-size: 0.8rem;
            font-weight: 700;
            margin-bottom: 16px;
        }
        .start-illustration {
            width: 100px;
            height: 100px;
            margin: 0 auto 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--option-bg);
            border: 2px solid var(--primary);
            border-radius: 0px;
            box-shadow: var(--card-shadow);
        }
        
        /* Bootstrap Style 12컬럼 구조 호환 그리드 시스템 구축 */
        .start-info-grid {
            display: grid;
            grid-template-columns: repeat(12, 1fr); /* 12컬럼 시스템 */
            gap: 24px; /* 표준 마진 간격 */
            margin-bottom: 32px;
            text-align: center;
        }
        .start-info-card {
            grid-column: span 4; /* 각각 4개 컬럼씩 나누어 차지 (합계 12) */
            background: var(--option-bg);
            border: 1px solid var(--option-border);
            padding: 16px 8px;
            border-radius: 0px;
        }
        .start-info-card span {
            display: block;
            color: var(--text-muted);
            font-size: 0.75rem;
            margin-bottom: 4px;
            font-weight: 700;
        }
        .start-info-card strong {
            font-weight: 700;
            color: var(--text-main);
        }

        /* 연산 로더 컴포넌트 */
        #loading-page {
            text-align: center;
            padding: 40px 0;
        }
        .loader-visualization {
            width: 60px;
            height: 60px;
            margin: 0 auto 24px;
            border: 4px solid var(--progress-bg);
            border-top-color: var(--primary);
            animation: spin 0.8s linear infinite;
        }
        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* 결과 창 뷰 */
        .result-header {
            text-align: center;
            margin-bottom: 32px;
        }
        .character-emoji {
            font-size: 4rem;
            display: inline-block;
            margin-bottom: 16px;
        }
        .mbti-tag {
            font-size: 3.2rem;
            font-weight: 700;
            color: var(--primary-dark);
            margin: 4px 0 12px;
            letter-spacing: 1px;
        }
        .result-desc-card {
            background: var(--option-bg);
            border: 1px solid var(--option-border);
            border-radius: 0px;
            padding: 24px;
            margin-bottom: 32px;
            box-shadow: var(--card-shadow);
        }
        .result-desc-text {
            font-size: 1.02rem;
            line-height: 1.6;
            color: var(--text-main);
            word-break: keep-all;
        }
        .trait-tags-container {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            justify-content: center;
            margin-top: 16px;
        }
        .trait-tag {
            background: var(--primary-light);
            color: var(--primary-dark);
            font-weight: 700;
            font-size: 0.85rem;
            padding: 6px 12px;
            border-radius: 0px;
            border: 1px solid var(--option-border);
        }

        /* 균형도 차트 레이아웃 */
        .dimension-row {
            margin-bottom: 20px;
        }
        .dimension-labels {
            display: flex;
            justify-content: space-between;
            margin-bottom: 6px;
            font-size: 0.9rem;
            font-weight: 700;
        }
        .dim-label.active {
            color: var(--primary-dark);
        }
        .dim-bar-wrapper {
            display: flex;
            height: 14px;
            background: var(--progress-bg);
            border: 1px solid var(--primary);
            border-radius: 0px;
            overflow: hidden;
        }
        .dim-bar-left, .dim-bar-right {
            height: 100%;
            transition: width 0.6s ease;
        }
        .dim-bar-left { background: var(--accent-gradient); }
        .dim-bar-right { background: var(--progress-bg-secondary); }

        .dim-row-right .dim-bar-left { background: var(--progress-bg-secondary); }
        .dim-row-right .dim-bar-right { background: var(--accent-gradient); }

        /* 매칭 파트너스 그라데이션 */
        .compatibility-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin-bottom: 32px;
        }
        .comp-card {
            background: var(--option-bg);
            border: 1px solid var(--option-border);
            border-radius: 0px;
            padding: 16px;
            text-align: center;
            transition: transform 0.15s ease-out;
        }
        .comp-card:hover {
            transform: scale(1.02);
            border-color: var(--primary);
            box-shadow: var(--card-shadow);
        }
        .comp-mbti {
            font-size: 1.25rem;
            font-weight: 700;
            color: var(--primary-dark);
        }

        /* 액션 하단 버튼 그룹 */
        .result-actions {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .btn-secondary-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }
        .btn-sec {
            background: var(--option-bg);
            color: var(--text-main);
            border: 1px solid var(--option-border);
            padding: 14px;
            border-radius: 0px;
            cursor: pointer;
            font-weight: 700;
            transition: all 0.15s ease-out;
        }
        .btn-sec:hover {
            border-color: var(--primary);
            background: var(--option-hover-bg);
            transform: scale(1.02);
        }

        /* 프리미엄 윈도우 모달 */
        .modal {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            background: rgba(131, 24, 67, 0.4); /* 핑크 오버레이 단색 조율 */
            display: flex; justify-content: center; align-items: center;
            z-index: 1000; opacity: 0; pointer-events: none;
            transition: opacity 0.25s ease; padding: 20px;
        }
        .modal.active { opacity: 1; pointer-events: auto; }
        .modal-content {
            background: var(--card-bg);
            border: 2px solid var(--primary);
            border-radius: 0px;
            padding: 32px;
            width: 100%; max-width: 440px;
            box-shadow: var(--card-shadow);
            position: relative;
        }
        .modal-close-btn {
            position: absolute; top: 16px; right: 16px;
            background: var(--badge-bg); border: 1px solid var(--primary);
            width: 32px; height: 32px; border-radius: 0px; cursor: pointer;
        }

        /* 여권 카드 프리뷰 디자인 컴포넌트 */
        .card-preview-area {
            display: flex; justify-content: center; margin-bottom: 20px;
        }
        .premium-pass-preview {
            width: 280px; height: 380px;
            background: var(--accent-gradient);
            border-radius: 0px; padding: 24px;
            color: white; display: flex; flex-direction: column;
            justify-content: space-between; position: relative;
            border: 2px solid white;
        }

        /* 안내 토스트 바 */
        .custom-toast {
            position: fixed; bottom: -60px; left: 50%;
            transform: translateX(-50%);
            background: var(--primary-dark); color: white;
            font-weight: 700; padding: 12px 24px;
            border-radius: 0px; z-index: 2000; opacity: 0;
            transition: all 0.3s ease;
        }
        .custom-toast.show { bottom: 40px; opacity: 1; }

        /* 📱 Adaptive 반응형 전략: 디바이스 그리드 이중 설계 */
        @media (max-width: 768px) {
            body { padding: 40px 16px; }
            .app-container { padding: 28px 20px; }
            .start-info-grid { 
                grid-template-columns: repeat(12, 1fr); 
                gap: 12px; 
            }
            .start-info-card { 
                grid-column: span 12; /* 모바일 전용 세로 정렬 자동 스위칭 */
            }
            .compatibility-section { grid-template-columns: 1fr; }
            .btn-secondary-group { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <div class="glow-orb orb-1"></div>
    <div class="glow-orb orb-2"></div>

    <div class="app-container">
        <div class="header-bar">
            <button id="btn-back" class="btn-back" onclick="goBack()">이전으로</button>
            <div class="header-controls">
                <button class="sound-toggle" id="sound-btn" onclick="toggleSound()">🔇</button>
                <button class="theme-toggle" onclick="toggleTheme()">🌙</button>
            </div>
        </div>

        <div id="start-page" class="page active">
            <div class="result-header">
                <div class="start-illustration"><span style="font-size: 3rem;">💗</span></div>
                <div class="start-badge">VIBRANT PINK SYSTEM</div>
                <h1 style="font-size: 1.9rem; font-weight: 700; margin-bottom: 12px; word-break: keep-all;">정밀 성격유형 진단 테스트</h1>
                <p style="color: var(--text-muted); font-size: 1rem; margin-bottom: 32px; word-break: keep-all;">
                    설계된 UI 마크다운 규칙에 기반하여, 세련된 비주얼 연산 엔진을 통한 나만의 MBTI 정밀 프로파일링 리포트를 생성합니다.
                </p>
            </div>

            <div class="start-info-grid">
                <div class="start-info-card"><span>문항 수</span><strong>12 문항</strong></div>
                <div class="start-info-card"><span>인터랙션</span><strong>0.15s Scale</strong></div>
                <div class="start-info-card"><span>레이아웃</span><strong>768px 맥스</strong></div>
            </div>

            <button class="btn-main" onclick="startTest()">진단 시작하기 ➔</button>
        </div>

        <div id="question-page" class="page">
            <div class="progress-wrapper">
                <div class="progress-header">
                    <span class="progress-text">성향 리포트 빌드 프로세싱</span>
                    <span class="progress-percent-bubble" id="progress-percent">1 / 12</span>
                </div>
                <div class="progress-bg"><div class="progress-fill" id="progress-fill-bar"></div></div>
            </div>
            <div id="question-content">
                <div class="question-title" id="question-title-text">데이터 동기화 중...</div>
                <div id="options-container"></div>
            </div>
        </div>

        <div id="loading-page" class="page">
            <div class="loader-visualization"></div>
            <div style="font-size: 1.15rem; font-weight: 700; margin-bottom: 8px;">성향 변수 최적화 데이터 연산 중...</div>
            <div style="color: var(--text-muted); font-size: 0.9rem;">Adaptive 반응형 구조 및 스타일 엔진을 준비 중입니다.</div>
        </div>

        <div id="result-page" class="page">
            <div class="result-header">
                <span class="character-emoji" id="result-emoji">👑</span>
                <p style="color: var(--text-muted); font-size: 0.9rem; font-weight: 700; letter-spacing: 1px;">분석 완료 · 최종 성격 진단</p>
                <div class="mbti-tag" id="mbti-type-tag">결과 로딩</div>
                <h2 id="mbti-title-text" style="font-size: 1.35rem; font-weight: 700; margin-bottom: 12px;"></h2>
            </div>

            <div class="result-desc-card">
                <p class="result-desc-text" id="mbti-description"></p>
                <div class="trait-tags-container" id="trait-tags-box"></div>
            </div>

            <div class="result-desc-card">
                <h3 style="font-size: 1.05rem; margin-bottom: 20px;">📊 성향 도메인 밸런스 상세 데이터</h3>
                <div id="dimension-charts-zone"></div>
            </div>

            <div class="compatibility-section">
                <div class="comp-card" id="best-partner-box">
                    <div style="font-size: 0.75rem; font-weight: 700; color: var(--success); margin-bottom: 4px;">BEST CHEMISTRY</div>
                    <div class="comp-mbti" id="best-comp-mbti">----</div>
                    <div style="font-size: 0.8rem; color: var(--text-muted);" id="best-comp-name">연산 오류</div>
                </div>
                <div class="comp-card" id="worst-partner-box">
                    <div style="font-size: 0.75rem; font-weight: 700; color: var(--error); margin-bottom: 4px;">WORST CHEMISTRY</div>
                    <div class="comp-mbti" id="worst-comp-mbti">----</div>
                    <div style="font-size: 0.8rem; color: var(--text-muted);" id="worst-comp-name">연산 오류</div>
                </div>
            </div>

            <div class="result-actions">
                <button class="btn-main" onclick="openPassModal()">🎫 프리미엄 진단 인증 패스 발급</button>
                <div class="btn-secondary-group">
                    <button class="btn-sec" onclick="copyShareUrl()">🔗 결과 주소 복사</button>
                    <button class="btn-sec" onclick="resetTest()">🔄 테스트 다시하기</button>
                </div>
            </div>
        </div>
    </div>

    <div class="modal" id="pass-modal">
        <div class="modal-content">
            <button class="modal-close-btn" onclick="closePassModal()">×</button>
            <h3 style="font-size: 1.15rem; margin-bottom: 20px; text-align: center;">Premium Pass Certification</h3>
            <div class="card-preview-area">
                <div class="premium-pass-preview">
                    <div>
                        <div style="font-size: 0.75rem; letter-spacing: 1px; opacity: 0.8;">OFFICIAL REPORT PASS</div>
                        <div style="font-size: 1.8rem; font-weight: 700; margin-top: 4px;" id="modal-pass-mbti">MBTI</div>
                    </div>
                    <div>
                        <div style="font-size: 0.85rem; font-weight: 500;" id="modal-pass-title">성향 분석 인증 완료</div>
                        <div style="font-size: 0.65rem; opacity: 0.7; margin-top: 4px;">Vibrant Pink UI System Standard</div>
                    </div>
                </div>
            </div>
            <button class="btn-main" style="padding: 12px;" onclick="triggerToast('Pass 발급 완료! (데모 데스크톱 전용)')">클라우드 패스 저장</button>
        </div>
    </div>

    <div class="custom-toast" id="toast-layer">알림 메시지</div>

    <script>
        // 12개 핵심 정밀 변수 문항 에셋 리스트 
        const questions = [
            { q: "새로운 테크 트렌드나 디자인 시스템을 보면 마음이 어떤가요?", a: "나도 모르게 흥분되고 직접 내 코드나 삶에 적용해보고 싶다.", b: "안정적이고 검증된 기존의 가이드라인을 먼저 따르는 편이다.", type: "EI" },
            { q: "프로젝트 일정을 짜거나 작업을 시작할 때 나의 성향은?", a: "세부적인 분량과 시간, 모서리 스펙까지 완벽한 계획을 미리 세운다.", b: "그때그때 흐름에 유연하게 맞추며 직관적인 트랜지션을 선호한다.", type: "SN" },
            { q: "동료가 코드 에러나 디자인 피드백으로 좌절하고 있을 때 내 첫 반응은?", a: "에러 로그의 논리적 모순을 찾아내고 해결 코드를 짚어준다.", b: "마음을 먼저 위로해주고 커피 한 잔을 마시며 멘탈을 챙겨준다.", type: "TF" },
            { q: "방 정리를 하거나 컴퓨터 폴더 정리 구조를 볼 때 나는?", a: "카테고리별, 날짜별 규칙이 칼같이 들어맞아야 마음이 편안하다.", b: "자유로운 배치 속에서 나만의 직관으로 파일들을 찾아낸다.", type: "JP" },
            { q: "주말이나 휴일에 나에게 가장 완벽한 에너지를 주는 활동은?", a: "다양한 사람들과 테크 컨퍼런스에 참여해 대화하고 자극을 받는다.", b: "조용한 여백의 방에서 혼자 음악을 들으며 나만의 시스템을 조율한다.", type: "EI" },
            { q: "디자인 시안을 볼 때 내가 먼저 주목하는 시각 요소는?", a: "정확한 픽셀 그리드, 여백 수치, 컴포넌트의 논리적 구조", b: "전체적인 색감이 주는 분위기와 감성적인 인터랙션 피드백", type: "SN" },
            { q: "중요한 결정을 내려야 하는 회의 상황에서 나는?", a: "객관적인 수치 자료와 성능 벤치마크 데이터를 최우선으로 본다.", b: "이 결정이 팀원들의 기분과 유저 경험에 미칠 심리적 영향을 고려한다.", type: "TF" },
            { q: "약속 시간이나 마감 기한이 다가올 때 내 행동 양식은?", a: "마감일보다 훨씬 여유 있게 작업을 완료해야 스트레스가 없다.", b: "벼락치기 같은 강력한 집중력으로 마감 직전에 폭발적인 효율을 낸다.", type: "JP" },
            { q: "낯선 모임이나 새로운 조별 과제 환경에 투입되었을 때 나는?", a: "먼저 말을 건네며 분위기를 주도하고 아이스브레이킹을 이끈다.", b: "상황을 조용히 관찰하며 내 역할이 주어질 때까지 기다린다.", type: "EI" },
            { q: "소설이나 영화를 볼 때 내가 더 몰입하는 부분은?", a: "치밀하게 짜인 복선, 현실적인 설정과 개연성이 높은 전개", b: "인물들의 감정선, 비현실적이더라도 아름답고 상상력 풍부한 세계관", type: "SN" },
            { q: "팀원의 작업 결과물에 아쉬운 점이 보일 때 피드백 스타일은?", a: "개선해야 할 점을 가감 없이 명확하게 팩트 위주로 지적한다.", b: "상대방의 노력을 먼저 칭찬한 후 조심스럽게 의견을 제안한다.", type: "TF" },
            { q: "여행을 떠나기 전, 내가 작성하는 계획표의 밀도는?", a: "몇 시에 어느 식당을 가고 이동 수단은 무엇인지 엑셀로 기록한다.", b: "대략적인 목적지 몇 개만 정해두고 발길 닿는 대로 움직인다.", type: "JP" }
        ];

        // 16가지 성격 유형 도출 알고리즘 딕셔너리 매핑 데이터
        const mbtiResults = {
            "ESTJ": { title: "전형적인 정밀 설계 마스터", desc: "엄격한 논리와 규칙, 완벽한 그리드 시스템을 기반으로 효율적인 컴포넌트를 빌드하는 기획자형입니다.", emoji: "👔", traits: ["체계적", "규칙중시", "강력한리더십"] },
            "ENTJ": { title: "대담한 전략적 혁신가", desc: "Vibrant Pink의 강렬한 에너지를 리더십으로 승화하여 거대한 아키텍처와 비즈니스 레이아웃을 진두지휘합니다.", emoji: "🦅", traits: ["전략적", "목표지향", "추진력"] },
            "ESFJ": { title: "친절한 조화의 아키텍트", desc: "주변 사람들과의 따뜻한 관계 속에서 표준 가이드라인을 제공하며, 협업 환경을 럭셔리하게 정돈합니다.", emoji: "🤝", traits: ["사교적", "협력가", "공감능력"] },
            "ENFJ": { title: "이상적인 정의의 카리스마", desc: "사람들을 성장시키는 가치 있는 목표를 위해 감성적인 디자인과 강력한 스케일 인터랙션 피드백을 전달합니다.", emoji: "🔥", traits: ["영향력", "이타적", "성장지원"] },
            "ESTP": { title: "스릴을 즐기는 가속 엔지니어", desc: "복잡한 이론보다 눈앞의 문제를 빠르게 해결하는 12컬럼 부트스트랩 그리드 같은 실천형 해결사입니다.", emoji: "🏍️", traits: ["실전파", "적응력", "위기해결"] },
            "ENTP": { title: "뜨거운 논쟁의 아이디어 뱅크", desc: "기존의 틀을 깨는 모서리 0px의 날카롭고 참신한 솔루션으로 세상을 뒤흔들 새로운 트렌드를 제시합니다.", emoji: "💡", traits: ["창의적", "다재다능", "토론가"] },
            "ESFP": { title: "자유로운 영혼의 비주얼 스타", desc: "인생이라는 무대에서 트렌디한 핑크 컬러 팔레트처럼 에너지를 발산하며 주변을 즐겁게 만드는 주인공입니다.", emoji: "🎉", traits: ["낙천적", "시각화", "친화력"] },
            "ENFP": { title: "재기발랄한 감성 크리에이터", desc: "자유롭고 부드러운 그라데이션 원형처럼 끝없는 상상력을 바탕으로 사람들의 마음을 움직이는 UI를 만듭니다.", emoji: "🦄", traits: ["열정적", "아이디어", "자유인"] },
            "ISTJ": { title: "신뢰감 있는 청렴한 감리사", desc: "본고딕 코포레이트 폰트처럼 묵직하고 정직하게 약속을 지키며, 백엔드와 프론트의 보이지 않는 최적화를 이룹니다.", emoji: "📐", traits: ["철저함", "약속엄수", "현실적"] },
            "INTJ": { title: "용의주도한 시스템 아키텍트", desc: "맥스 가로폭 768px 내부의 완벽한 최적화 알고리즘을 독자적으로 빌딩하는 차가운 지성의 설계자입니다.", emoji: "🔮", traits: ["독립적", "치밀함", "장기전략"] },
            "ISFJ": { title: "수호자형 프리미엄 서포터", desc: "뒤로가기 버튼처럼 언제나 보이지 않는 곳에서 시스템 안정성을 테스트하고 지원하는 가장 따뜻한 방어벽입니다.", emoji: "🛡️", traits: ["헌신적", "세심함", "안정지향"] },
            "INFJ": { title: "통찰력 있는 내면의 예언자", desc: "깊은 다크 모드 속에서 우아하게 반짝이는 빛처럼 사람들의 본질적인 마인드를 읽어내는 고요한 철학자입니다.", emoji: "🎐", traits: ["통찰력", "신비로움", "이상주의"] },
            "ISTP": { title: "만능 장인 테크니컬 마스터", desc: "도구와 기계를 능숙하게 다루며, 불필요한 코드를 모두 걷어내는 익스트림 성능 최적화 전문가입니다.", emoji: "🛠️", traits: ["분석적", "효율성", "냉철함"] },
            "INTP": { title: "논리적인 사색의 AI 개발자", desc: "현상 뒤에 숨겨진 구조와 변수의 본질을 분석하며 데이터 추상화 레이어를 정밀 가공하는 순수 지식인입니다.", emoji: "🔬", traits: ["아이디어", "객관적", "비판적"] },
            "ISFP": { title: "성인군자형 감성 아티스트", desc: "말없이 은은한 여백의 미를 추구하며, 나만의 작은 컴포넌트 공간 속에서 세상을 예술적으로 음미합니다.", emoji: "🎨", traits: ["예술가", "온화함", "미적감각"] },
            "INFP": { title: "잔망스러운 낭만 프로그래머", desc: "Vibrant Pink 컬러 속에서 자신만의 따뜻한 세계관과 스토리를 코드로 녹여내는 이상주의적 낭만파입니다.", emoji: "🐳", traits: ["낭만적", "이상주의", "깊은내면"] }
        };

        // 매칭 테이블 세팅 데이터
        const chemistryMap = {
            "ESTJ": { best: "INTP", worst: "INFP" }, "ENTJ": { best: "INFP", worst: "ISFP" },
            "ESFJ": { best: "ISFP", worst: "INTJ" }, "ENFJ": { best: "INFP", worst: "ISTP" },
            "ESTP": { best: "ISFJ", worst: "INFJ" }, "ENTP": { best: "INFJ", worst: "ISFJ" },
            "ESFP": { best: "ISFJ", worst: "INTJ" }, "ENFP": { best: "INFJ", worst: "ISTJ" },
            "ISTJ": { best: "ESFP", worst: "ENFP" }, "INTJ": { best: "ENFP", worst: "ESFP" },
            "ISFJ": { best: "ESFP", worst: "ENTP" }, "INFJ": { best: "ENFP", worst: "ESTP" },
            "ISTP": { best: "ESFJ", worst: "ENFJ" }, "INTP": { best: "ESTJ", worst: "ESFJ" },
            "ISFP": { best: "ENFJ", worst: "ENTJ" }, "INFP": { best: "ENTJ", worst: "ESTJ" }
        };

        let currentIdx = 0;
        let answers = [];
        let isSoundActive = false;

        // 사운드 시뮬레이션 인터랙션 
        function toggleSound() {
            isSoundActive = !isSoundActive;
            document.getElementById("sound-btn").innerText = isSoundActive ? "🔊" : "🔇";
            triggerToast(isSoundActive ? "피드백 사운드가 동기화되었습니다." : "사운드가 차단되었습니다.");
        }

        // 테마 스위칭 프로세스
        function toggleTheme() {
            const body = document.body;
            body.classList.toggle("dark-theme");
            const isDark = body.classList.contains("dark-theme");
            triggerToast(isDark ? "Luxury Dark Pink 테마 가동" : "Vibrant Light Pink 테마 가동");
        }

        // 테스트 이니셜라이징
        function startTest() {
            currentIdx = 0;
            answers = [];
            switchPage("start-page", "question-page");
            document.getElementById("btn-back").style.visibility = "visible";
            renderQuestion();
        }

        // 라우팅 스위칭
        function switchPage(from, to) {
            document.getElementById(from).classList.remove("active");
            document.getElementById(to).classList.add("active");
        }

        // 라우팅 백트래킹 (이전으로)
        function goBack() {
            if (currentIdx > 0) {
                currentIdx--;
                answers.pop();
