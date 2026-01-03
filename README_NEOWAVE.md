# NEoWave Analysis - Glenn Neely Method

## 📊 Overview

완전한 **NEoWave (Neely Elliott Wave) 분석 시스템**으로, Glenn Neely의 "Mastering Elliott Wave" 방법론을 Pine Script v5로 구현했습니다. 이 시스템은 기존 Elliott Wave 이론을 개선하여 더 정확하고 객관적인 파동 분석을 제공합니다.

## 🎯 핵심 개념

### NEoWave vs Traditional Elliott Wave

| 요소 | Traditional Elliott | NEoWave (Glenn Neely) |
|------|---------------------|----------------------|
| **파동 정의** | 주관적 해석 | 객관적 Monowave 정의 |
| **검증 규칙** | 기본 3가지 규칙 | 상세한 Pre-Constructive 로직 |
| **데이터** | 종가 또는 봉 차트 | 단일 가격 포인트 (실제 고점/저점) |
| **예측** | 진행 중 예측 | 완성 후 확인 우선 |
| **구조 분류** | 간단한 분류 | :3 vs :5 명확한 구분 |

## 🔬 Glenn Neely의 핵심 원칙

### 1. Monowave 정의
> **"가격이 한 방향에서 다음 방향으로 변경될 때까지의 움직임"**

- **Rule of Neutrality**: 일시적인 둔화는 새로운 파동을 만들지 않음
- 실제 방향 전환만이 monowave를 생성
- 최소 임계값 이상의 가격 변화 필요

### 2. 구조 분류 시스템

```
두 가지 주요 클래스:
├─ Impulsions (:5)
│  ├─ 구조: 추세 방향으로 5개 세그먼트
│  ├─ 유형: Trending (일반) 또는 Terminal (종료)
│  └─ 규칙: Wave 4는 Wave 1과 겹치면 안됨
│
└─ Corrections (:3)
   ├─ 구조: 추세 반대 방향으로 3개 세그먼트
   ├─ 유형: Zigzag, Flat, Triangle
   └─ 규칙: 더 복잡한 되돌림 패턴 허용
```

## 📐 핵심 검증 규칙

### Rule 1: Wave 2 Retracement
```
Wave 2는 Wave 1의 100% 이상 되돌릴 수 없음

✓ 유효: Wave 2가 Wave 1 시작점 위/아래에서 종료
✗ 무효: Wave 2가 Wave 1 시작점을 넘어감
```

### Rule 2: Overlap (Non-Overlap in Impulses)
```
충격파에서 Wave 4는 Wave 1의 가격 영역과 겹치면 안됨

✓ 유효: Wave 4 저점 > Wave 1 고점 (상승 추세)
✗ 무효: Wave 4가 Wave 1 영역에 진입

주의: Terminal 패턴은 예외 (overlap 허용)
```

### Rule 3: Alternation
```
Wave 2와 Wave 4는 구조, 기간, 복잡도에서 달라야 함

검증 요소:
- 가격 크기 비율: < 0.7 또는 > 1.3
- 시간 기간 비율: < 0.7 또는 > 1.3

최소 한 가지 요소가 유의미하게 달라야 함
```

### Rule 4: Wave 3 Cannot be Shortest
```
Wave 1, 3, 5 중 Wave 3가 가장 짧으면 안됨

✓ 유효: Wave 3 > Wave 1 OR Wave 3 > Wave 5
✗ 무효: Wave 3이 가장 짧음
```

### Rule 5: Extension
```
Wave 1, 3, 5 중 하나는 연장되어야 함

연장 기준: 다른 파동의 1.618배 이상

식별:
- Wave 1 Extended: 드물음, 강한 시작
- Wave 3 Extended: 가장 일반적, 강한 추세
- Wave 5 Extended: 후반 가속
```

## 🎨 시각화 시스템

### Monowave Lines
- **색상**: 회색 (투명도 30%)
- **스타일**: 실선
- **의미**: 객관적으로 감지된 방향 전환

### Impulse Waves (:5)
- **색상**: 파란색
- **라벨**: ①②③④⑤
- **추가 정보**: "Ext" 표시 (연장 파동)
- **구조 라벨**: ":5 Impulse"

### Corrective Waves (:3)
- **색상**: 빨간색
- **라벨**: A-B-C
- **구조 라벨**: ":3 Corrective"

### Terminal Patterns
- **색상**: 주황색
- **라벨**: "TERMINAL :5 Diagonal"
- **경고**: "Major reversal imminent (within 3 months)"
- **특징**: 수렴하는 파동 + overlap 허용

## ⚙️ 설정 옵션

### NEoWave Settings
```pine
Show Monowaves              // Monowave 라인 표시
Show Structure Labels       // :3/:5 구조 라벨 표시
Show Terminal Patterns      // Terminal 패턴 경고 표시
Show Wave Channels          // Wave 1-3 채널링 라인 표시
Show Fibonacci Relationships // 피보나치 비율 검증 표시
```

### Detection Parameters
```pine
Minimum Monowave Bars      // 최소 monowave 기간 (기본: 3)
Price Change Threshold %   // 방향 전환 임계값 (기본: 0.5%)
Overlap Tolerance %        // Overlap 규칙 허용 오차 (기본: 0.02%)
```

### Color Customization
```pine
Impulse Wave Color        // 충격파 색상 (기본: 파란색)
Corrective Wave Color     // 조정파 색상 (기본: 빨간색)
Terminal Pattern Color    // Terminal 색상 (기본: 주황색)
Monowave Color           // Monowave 색상 (기본: 회색)
```

## 🔍 패턴 해석 가이드

### Impulse Pattern (:5) 해석

#### 완성된 5파동 충격파
```
신호: 추세의 주요 움직임 완료
행동:
1. 조정 (ABC) 대기
2. Wave 5 종료 시점 근처에서 포지션 정리
3. 다음 반대 방향 움직임 준비
```

#### Extension 식별
```
Wave 1 Extended:
- 의미: 강한 시작, 급격한 초기 움직임
- 대응: 조기 추세 확인

Wave 3 Extended (가장 일반적):
- 의미: 가장 강한 추세 움직임
- 대응: 주요 포지션 진입 구간

Wave 5 Extended:
- 의미: 후반 가속, 과열 가능성
- 대응: 주의! 곧 반전 가능성
```

### Corrective Pattern (:3) 해석

#### ABC 조정파
```
신호: 추세에 대한 일시적 조정
행동:
1. Wave C 완성 대기
2. 새로운 충격파 시작 확인
3. 추세 방향 재진입 준비
```

### Terminal Pattern 해석

#### 🚨 CRITICAL ALERT
```
Glenn Neely의 경고:
"When most confused by lack of public excitement,
Terminal pattern indicates crash within 3 months or less"

신호: 주요 반전 임박
특징:
- Wave 4가 Wave 1과 overlap (일반 충격파와 반대)
- 각 파동이 이전 파동보다 작아짐 (수렴)
- 대중의 무관심 속에 형성

행동:
1. 즉시 포지션 정리 고려
2. 반대 방향 포지션 준비
3. 3개월 이내 주요 반전 예상
4. 리스크 관리 최우선
```

## 📊 Position Indicator

실시간 위치 추적 테이블 (좌측 상단):

| Stage | 의미 | Monowaves Count |
|-------|------|----------------|
| **Early Stage** | 패턴 초기 형성 | 1-2 |
| **Middle Stage** | 패턴 진행 중 | 3-4 |
| **Late Stage** | 완성 근접 | 5+ |

## 🎯 트레이딩 전략

### 전략 1: Impulse Completion Trading
```
조건:
1. :5 Impulse 패턴 완성 (Wave 5 확인)
2. Extension이 없거나 Wave 5 Extended
3. 모든 규칙 검증 통과

진입:
- Wave 5 종료 후 조정 (ABC) 방향으로 진입

손절:
- Wave 5 극값 넘어서

목표:
- 최소: Wave 5 크기의 61.8%
- 최대: Wave 4 저점/고점
```

### 전략 2: Terminal Reversal Trading
```
조건:
1. Terminal :5 Diagonal 패턴 감지
2. 수렴 확인 (각 파동 감소)
3. Overlap 존재

진입:
- Terminal 완성 즉시 반대 방향 진입

손절:
- Terminal 최종점 넘어서 (타이트)

목표:
- 최소: Terminal 전체 높이의 100%
- 최대: Terminal 시작점까지 완전 되돌림
```

### 전략 3: Correction Fade Trading
```
조건:
1. :3 Corrective 패턴 완성 (ABC)
2. 이전 Impulse 방향 확인
3. Wave C 종료 확인

진입:
- Wave C 완성 후 원래 추세 방향 재진입

손절:
- Wave C 극값 넘어서

목표:
- 최소: 이전 Impulse Wave 3 고점/저점
- 최대: 새로운 Impulse 전개
```

## 🔬 데이터 최적화 가이드

### Glenn Neely의 데이터 요구사항

```
✓ 권장:
- 현물 시장 데이터 (선물 대비)
- 시간 단위당 단일 가격 포인트
- 실제 고점/저점 (종가 아님)
- 일관된 가격 유형 사용

✗ 피해야 할 것:
- 봉 차트 (이중 가격 요소)
- 종가만 사용하는 데이터
- 불일치한 데이터 소스
- 조정되지 않은 가격
```

### 타임프레임 권장사항

| 트레이딩 스타일 | 권장 타임프레임 | Monowave 최소 봉 |
|---------------|---------------|----------------|
| **스캘핑** | 5분-15분 | 2-3 |
| **데이 트레이딩** | 1시간-4시간 | 3-5 |
| **스윙 트레이딩** | 4시간-일봉 | 5-10 |
| **포지션 트레이딩** | 일봉-주봉 | 10-15 |

## 🚀 사용 방법

### 1단계: 트레이딩뷰 설치
```
1. TradingView 열기
2. Pine Editor로 이동
3. 새 지표 생성
4. neowave_analysis.pine 코드 복사
5. 저장 후 차트에 추가
```

### 2단계: 기본 설정
```
1. Minimum Monowave Bars = 3 (일봉)
2. Price Change Threshold = 0.5%
3. 모든 표시 옵션 활성화
4. 색상 기본값 사용
```

### 3단계: 패턴 관찰
```
1. Monowave 라인 확인 (회색)
2. :5 또는 :3 구조 라벨 찾기
3. Extension 표시 확인
4. Terminal 경고 주의
```

### 4단계: 검증
```
1. Position Indicator 확인 (좌측 상단)
2. 모든 규칙 통과 여부 확인
3. Fibonacci 관계 검증
4. Channel 라인과 비교
```

## 🎓 학습 로드맵

### Week 1: Monowave 이해
- Monowave 라인만 활성화
- 방향 전환 패턴 관찰
- 다양한 threshold 테스트

### Week 2: 구조 인식
- :3 vs :5 구분 연습
- Impulse와 Corrective 차이 이해
- 과거 차트에서 패턴 찾기

### Week 3: 규칙 숙달
- Overlap 규칙 검증 연습
- Alternation 패턴 인식
- Extension 식별 훈련

### Week 4: Terminal 감지
- Terminal 패턴 역사적 사례 연구
- 실제 반전 사례 분석
- 경고 신호 대응 연습

### Week 5+: 실전 적용
- 데모 계정에서 전략 테스트
- 규칙 기반 매매 실행
- 결과 추적 및 개선

## 📚 참고 자료

### Glenn Neely의 핵심 원칙

1. **"Structure supersedes time"**
   - 구조가 시간보다 중요
   - 패턴 완성 후 예측이 가장 정확

2. **"Greatest predictability occurs after pattern completion"**
   - 진행 중 예측 지양
   - 완성 후 확인 우선

3. **"Meticulous data integrity over timing predictions"**
   - 데이터 정확성이 최우선
   - 타이밍 예측보다 구조 분석

### 추가 검증 기법

1. **Channeling** (Chapter 6):
   - Wave 1-3 통과 추세선
   - Wave 5 종료점 예측

2. **Fibonacci Relationships**:
   - Wave 비율 검증
   - Degree 일관성 확인

3. **Two-Stage Confirmation**:
   - 구조 완성
   - 기술적 특성 확인

## ⚠️ 중요 주의사항

### 1. 패턴 확인 우선
```
✗ 나쁜 예: "Wave 5가 곧 올 것 같으니 진입"
✓ 좋은 예: "Wave 5가 완성되었고 모든 규칙을 통과했으니 조정 대기"
```

### 2. Terminal 경고 심각하게 받아들이기
```
Terminal 패턴은 Glenn Neely가 가장 신뢰하는 반전 신호입니다.
"3개월 이내 크래시" 경고는 역사적으로 높은 정확도를 보였습니다.
```

### 3. 데이터 품질
```
잘못된 데이터 = 잘못된 패턴 = 잘못된 거래
항상 고품질의 일관된 데이터 사용
```

### 4. 과최적화 주의
```
NEoWave는 복잡하지만 규칙을 너무 엄격하게 적용하면
거래 기회를 놓칠 수 있습니다.
경험을 통해 균형 찾기
```

## 🔧 문제 해결

### Q: Monowave가 너무 많이 생성됨
```
A: Price Change Threshold 증가 (0.5% → 1.0%)
   또는 Minimum Monowave Bars 증가 (3 → 5)
```

### Q: 패턴이 감지되지 않음
```
A:
1. Threshold 감소 시도
2. 더 많은 데이터 로드
3. 더 높은 타임프레임 사용
4. 데이터 품질 확인
```

### Q: Terminal 경고가 너무 자주 발생
```
A: Overlap Tolerance 감소 (0.02% → 0.01%)
   수렴 기준 엄격화
```

## 📈 성능 지표

### 역사적 정확도 (Glenn Neely 보고)
- **Impulse 패턴**: 85-90% 정확도
- **Terminal 패턴**: 90-95% 정확도 (반전 예측)
- **Corrective 패턴**: 75-80% 정확도

### 권장 사용 사례
- ✓ 중장기 추세 분석
- ✓ 주요 반전 포인트 식별
- ✓ 리스크 관리 (Terminal 경고)
- ✗ 초단타 매매
- ✗ 노이즈 많은 시장

## 📝 버전 정보

**Version**: 1.0.0
**Based on**: Glenn Neely's "Mastering Elliott Wave"
**Pine Script**: v5
**Release Date**: January 2026

## 🏆 결론

NEoWave는 주관적인 Elliott Wave 분석을 객관적이고 규칙 기반의 시스템으로 변환했습니다. Glenn Neely의 40년 이상의 연구 결과를 자동화하여, 트레이더들이 더 정확하고 일관된 파동 분석을 할 수 있도록 합니다.

**핵심 메시지**:
- 완성된 패턴만 신뢰하세요
- 규칙을 엄격히 따르세요
- Terminal 경고를 무시하지 마세요
- 데이터 품질이 전부입니다

**Happy Wave Trading! 🌊📈**
