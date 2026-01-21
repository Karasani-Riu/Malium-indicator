# Elliott Wave 이미지 분석 보고서
## Glenn Neely - Mastering Elliott Wave & NEoWaves

작성일: 2026-01-21
분석 대상:
- Mastering Elliott Wave OCR-1/2 (99개 이미지)
- NEoWaves 특수 패턴 (15개 이미지)

---

## 1. NEoWave 특수 패턴 (Glenn Neely 고급 이론)

### 1.1 Diametric Formation (다이메트릭 형성)

**패턴 정의:**
- 7-파동 구조 (A-B-C-D-E-F-G)
- Bow Tie 모양과 유사
- 상승 및 하강 추세선이 교차하는 형태
- 진정한 반전 패턴

**탐지 규칙:**
```
1. 명확한 7개 파동 구조 확인
2. 상층 추세선: 파동 A, C, E, G를 연결
3. 하층 추세선: 파동 B, D, F를 연결
4. 두 추세선이 교차하는 수렴점 확인
5. 파동 G는 일반적으로 상층 추세선을 돌파
```

**실제 예시:**
```
      G
     / \
    /   \___
   /E      \
  / \      F \
 /C  \    /   \___
/__B__\D /
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// 7개 파동 감지
// 상/하 추세선 생성
// 교차점 계산
// Bow-Tie 수렴 확인
```

---

### 1.2 Extracting Triangle (추출 삼각형)

**패턴 정의:**
- 5-파동 ABC 구조 (또는 ABCDE)
- 각 연속적인 하강이 가격상 더 작음
- 각 연속적인 상승이 가격상 더 큼
- Wave-C가 Wave-D보다 큼 (중요한 특징)
- Wave-D가 가장 복잡한 구조 (subdivided)

**탐지 규칙:**
```
1. Wave-A > Wave-C > Wave-E (하강측면)
2. Wave-B < Wave-D (상승측면)
3. Wave-B와 Wave-D 사이 시간 비율 확인
4. Wave-D 내부에 많은 세분화 발생
5. Wave-C는 항상 Wave-D보다 큼
```

**패턴 특징:**
- 가장 길고 복잡한 수정파동
- 시각적으로는 불규칙해 보임
- Wave-B가 항상 Wave-D보다 작음

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// Wave 길이 비교
// A > C > E 확인
// B < D 확인
// Wave-D subdivisions 감지
```

---

### 1.3 Neutral Triangle (중립 삼각형)

**패턴 정의:**
- 5-파동 ABC 구조
- 상승 파동(A, C, E): 지속적으로 좌에서 우로 수축 (contracting bias)
- 하강 파동(B, D): 확장 편향 (expanding bias)
- 중립적 추세 방향

**탐지 규칙:**
```
1. 상승 파동들의 진폭이 감소 (contracting)
2. 하강 파동들의 진폭이 증가 (expanding)
3. 전체 패턴은 비교적 범위 내에서 진행
4. 명확한 방향성이 없음
```

**특징:**
- 상층 추세선: 하강각도
- 하층 추세선: 상승각도
- 두 선이 미래의 한 점으로 수렴

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// 상승/하강 파동 진폭 추적
// 수축/확장 바이어스 계산
// 추세선 수렴 예측
```

---

### 1.4 5th Failure Terminal (5차 실패 종료)

**패턴 정의:**
- Impulse 패턴의 특수한 변형
- Wave-5가 Wave-4 최고값을 돌파하지 못함
- Wave-4와 Wave-1의 위치 차이가 중요한 특징

**탐지 규칙:**
```
1. Wave-5 < Wave-4 (가격 면에서)
2. Wave-4 최고값을 기준으로 확인
3. Wave-1 위치와 Wave-4 관계 분석
4. Termination point는 특정 Fibonacci 수준
```

**중요성:**
- 추세 반전의 강한 신호
- 약세 펄스의 징후

**PineScript 구현 가능성:** ⭐⭐⭐ (중간)
```python
// Wave 극값 비교
// Wave-4 vs Wave-5 위치
// Wave-1 위치 기준점 확인
```

---

### 1.5 Spike High/Low 패턴

**패턴 정의:**
- Diametric Formation 내에서의 특수한 구조
- 급격한 상승 또는 하강 형성
- Spike High: 상층 추세선 위의 급격한 상승
- Spike Low: 하층 추세선 아래의 급격한 하강

**탐지 규칙:**
```
1. 상층 추세선 설정 (highs 연결)
2. 하층 추세선 설정 (lows 연결)
3. 상승 스파이크: 가격이 상층선 위로 돌파
4. 하강 스파이크: 가격이 하층선 아래로 돌파
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// 추세선 계산
// 돌파 감지
```

---

### 1.6 Impulse 패턴의 Common Behavior 실수들

**실수 1: Second Advance Takes Too Much Time**
- 문제: 2차 상승이 보정 파동에 비해 너무 많은 시간 소요
- 감지: 시간 비율이 비정상적으로 불균형
- 해석: 추세의 약세 신호

**실수 2: Second Advance Too Violent**
- 문제: 2차 상승이 너무 급격하게 시작
- 원형 표시로 시작점 확인
- 해석: 강한 피크를 형성할 가능성 높음

**실수 3: Wave-C Has Not Taken Enough Time**
- 문제: Wave-C(또는 Wave-3)가 충분한 시간을 소비하지 않음
- 기준: A+B 시간의 약 50% 이상 필요
- 해석: 추세 약화 신호

**PineScript 구현 가능성:** ⭐⭐⭐ (중간)
```python
// 파동 시간 비율 계산
// 속도 분석 (가격/시간)
// 이상 패턴 플래그
```

---

## 2. Mastering Elliott Wave 기본 규칙 및 패턴

### 2.1 Monowave (모노파동) 개념

**정의:**
- 가장 작은 단위의 파동 구조
- 방향 변화 시작점에서 다음 방향 변화까지의 가격 움직임
- 모든 파동은 모노파동들로 구성됨

**특징:**
```
- 시작: 이전 추세에서 방향 변화
- 끝: 다음 방향 변화 시작
- 시간 단위: 중요하지 않음 (5분, 1시간, 1일 모두 가능)
- 정확한 식별: Elliott Wave 분석의 기초
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// ZigZag 감지로 방향 변화 식별
// 극값(High/Low) 기반 Monowave 구성
// 다중 시간대 검증
```

---

### 2.2 Rule of Neutrality (중립성 규칙)

**핵심 개념:**
- 모노파동 간의 각도 관계 분석
- 46도(약 1:1) 비율의 중요성

**규칙:**
```
1. 약간의 각도 변화는 무시 가능
2. 명확한 각도 변화 = 새로운 파동 구조
3. 2개 연속 모노파동의 각도 ≠ 직선으로 간주
4. 버스 동크 테스트: 3개 모노파동이 직선상에 있는지 확인
```

**비율 관계:**
- 46도 기준: 약 1:1 비율
- 45도 이상 = 명확한 방향 변화
- 45도 이하 = 연속적 추세 가능성

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// 연속 바(bar) 간의 각도 계산
// atan2() 함수 사용
// 45도 임계값 설정
```

---

### 2.3 Elliott Wave 파동 카운팅 규칙 (Rules 1-7)

#### Rule 1 - Activation Requirement
**규칙:**
- m0 = 어느 길이든 가능 (보통 0% ~ 201.8%)
- m0를 기초로 61.8% 이상 ~ 38.26% 미만 구간으로 구성 가능

**감지:**
```
1. 첫 파동(m0) 식별
2. 61.8% Fibonacci 극값 설정
3. 38.26% 극값 설정
4. m1 길이가 위 범위 내에 있는지 확인
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐⭐ (매우 높음)
```python
// m0 = wave[0]의 길이
// m1 >= m0 * 0.618 확인
// m1 <= m0 * 2.618 확인
```

#### Rule 4 - Condition Identification

**Rule 4:**
```
백분율 관계: m1 to m1 비율
- m2는 m1 길이의 100% ~ 261.8% 범위
- m2는 m1 길이의 38.2% ~ 261.8% 범위 (조정)
```

**Rule 4b:**
```
특정 조건:
- m3 >= 100% m1 기준
- m3 <= 38.2% m1 기준
- 이 관계가 Rule 4b의 핵심
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// m1 길이 기준점 설정
// m2 범위 확인 (1.0 ~ 2.618)
// m3 제약조건 확인
```

#### Rule 7 - Extension Pattern

**특징:**
```
1. m1의 261.8%까지 연장 가능
2. m3의 내부 세분화 구조
3. 활성화 요구사항 충족 필수
```

**감지 조건:**
```
- m1 극값에서 261.8% 이상 연장
- 내부 파동 구조 분석
- 시간 비율 검증
```

**PineScript 구현 가능성:** ⭐⭐⭐ (중간)
```python
// m1 길이 * 2.618 계산
// 현재 가격과 비교
// 확장 패턴 플래그
```

---

### 2.4 Advanced Wave Extensions & Failures

#### 5th Extension Impulse (5차 연장 임펄스)
**특징:**
- Wave-5가 일반적인 범위 초과로 연장
- 강한 추세의 신호
- 진폭이 Wave-1과 Wave-3보다 큼

**패턴:**
```
    5ext
      /
    3 /
   / \
  /   \
 1     4
```

**탐지:**
```
Wave-5 > Wave-3 가격상
Wave-5 > Wave-1 가격상
연장 비율: 일반적으로 161.8% 이상
```

#### Double Extension Impulse (극히 드문)
**특징:**
- 거의 불가능한 패턴
- Wave-5와 Wave-1 모두 161.8% 이상 연장
- 매우 강한 추세 신호

#### Failure 패턴 (8가지)

**1. Common Flat:**
- Wave-b가 Wave-a와 거의 같은 높이
- Wave-c가 Wave-b 아래로 하강

**2. Elongated Flat:**
- Wave-b가 Wave-a를 초과
- Wave-c가 더 낮음

**3. C-Failure:**
- Wave-c가 Wave-a 수준 미만
- 약세 신호

**4. B-Failure:**
- Wave-b가 Wave-a 수준 이하
- 매우 약한 구조

**5. Rare Double Failure:**
- Wave-b와 Wave-c 모두 실패
- 극히 드문 패턴

**6. Irregular Pattern:**
- Wave-b > Wave-a
- Wave-c > Wave-b
- 일반적인 Flat 확장

**7. Irregular Failure:**
- Wave-b > Wave-a
- Wave-c < Wave-a
- 약한 신호

**8. Running Pattern:**
- Wave-b 매우 강함
- Wave-c 약함
- 강한 기저 추세 신호

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// Wave-a, b, c 극값 비교
// 비율 관계 계산
// 8가지 패턴 분류
```

---

### 2.5 Triangle Patterns (삼각형 패턴)

#### Double Zigzag & Triple Zigzag

**특징:**
- 복수의 Zigzag 연결 구조
- 각 Zigzag 간 수평 또는 경사 분리
- Complex Correction의 일부

**패턴:**
```
Double Zigzag:      Triple Zigzag:
    X                   X    Y
   /\                  /\   /\
  /  \                /  \ /  \
 a    c    a    c    a c a c a c
```

**탐지:**
```
1. 첫 Zigzag 완성 (5-3-5)
2. 분리 파동(X) 식별
3. 두 번째 Zigzag 확인
4. 필요시 세 번째 Zigzag 추가
```

**PineScript 구현 가능성:** ⭐⭐⭐ (중간)
```python
// 각 Zigzag 패턴 감지
// 분리 파동 식별
// 패턴 조합 검증
```

---

### 2.6 Wave-Flat Patterns (플랫 패턴)

**플랫 비율 관계:**

**Elongated Flat:**
```
b/a >= 1.00
비율: 일반적으로 1.00 ~ 1.382
```

**Common Flat:**
```
b/a ≈ 1.00 ± 0.05 (±5%)
가장 일반적인 형태
```

**Compressed Flat:**
```
b/a <= 0.618
가격상 약한 반등
```

**Internal Relationships:**
```
Wave-a와 Wave-c의 길이 비율:
- 0.618 (61.8%)
- 1.000 (100%)
- 1.382 (138.2%)
```

**PineScript 구현 가능성:** ⭐⭐⭐⭐ (높음)
```python
// Wave-a 길이 계산
// Wave-b 높이 비율 계산
// Wave-c 관계 검증
```

---

## 3. 파인스크립트 구현 가능성 평가

### 3.1 구현 가능성 매트릭스

| 패턴 | 난이도 | 신뢰성 | 권장순위 | 구현시간 |
|------|-------|-------|---------|---------|
| Monowave 감지 | 쉬움 | 높음 | 1순위 | 2-3시간 |
| Rule of Neutrality | 중간 | 높음 | 2순위 | 3-4시간 |
| Fibonacci Ratios | 쉬움 | 매우높음 | 3순위 | 1-2시간 |
| Diametric Formation | 어려움 | 중간 | 4순위 | 8-10시간 |
| Extracting Triangle | 어려움 | 높음 | 5순위 | 6-8시간 |
| Neutral Triangle | 중간 | 중간 | 6순위 | 4-5시간 |
| Failure Patterns | 중간 | 높음 | 7순위 | 5-6시간 |
| Wave Extensions | 중간 | 높음 | 8순위 | 3-4시간 |

---

### 3.2 기술 구현 전략

#### 1단계: 기초 감지 시스템 (우선순위 높음)
```pinescript
// ZigZag 기반 Monowave 감지
// Fibonacci 비율 계산
// Rule of Neutrality 각도 분석
```

#### 2단계: 파동 검증 시스템 (우선순위 중간)
```pinescript
// Rules 1-7 조건 검증
// Wave 비율 관계 확인
// Internal Relationships 분석
```

#### 3단계: 고급 패턴 감지 (우선순위 낮음)
```pinescript
// Diametric Formation 감지
// Extracting Triangle 식별
// Failure Pattern 분류
```

---

## 4. 현재 advanced_market_analysis.pine 분석

### 4.1 이미 구현된 패턴

```
✓ Elliott Wave Basics (1-5 waves)
✓ ABC Corrective Waves
✓ Diagonal Patterns
✓ Triangle Waves
✓ Alternation Rules
✓ Extension Relationships
✓ Elliott Wave Channels
```

### 4.2 추가 구현 가능한 패턴 (신규)

```
★ NEW - Diametric Formation (7-wave)
★ NEW - Extracting Triangle (명확한 규칙)
★ NEW - Neutral Triangle (바이어스 기반)
★ NEW - 5th Failure Terminal
★ NEW - Wave Failure Classifications (8가지)
★ NEW - Advanced Extensions (5th, Double)
★ NEW - Spike High/Low Detection
★ NEW - Precise Fibonacci Internal Relationships
★ NEW - Common Behavior Mistakes Detection
```

---

## 5. 구현 권장사항

### 5.1 즉시 구현 권장 (1주일)

1. **Monowave 감지 개선**
   - 현재 ZigZag보다 정교한 방향변화 감지
   - Rule of Neutrality 각도 적용

2. **Fibonacci 비율 검증**
   - 규칙 1-7의 수학적 조건 자동화
   - 범위 기반 필터링

3. **Wave Failure 패턴**
   - 8가지 Failure 분류 자동화
   - 약세 신호 플래그

### 5.2 단계별 구현 (1개월)

**Week 1-2:**
- Monowave + Neutrality 강화
- Fibonacci 비율 기본 검증

**Week 3:**
- Failure 패턴 분류
- Extension 패턴 감지

**Week 4:**
- Diametric Formation 기본 구조
- Extracting Triangle 규칙 적용

---

## 6. 핵심 탐지 알고리즘

### 6.1 ZigZag 기반 Wave 감지 (권장)

```pinescript
// 1. 방향변화점 식별 (Monowave 경계)
direction_change = (high[i-1] > high[i] AND high[i] < high[i+1]) OR
                   (low[i-1] < low[i] AND low[i] > low[i+1])

// 2. Wave 크기 검증
wave_size = math.abs(high - prev_high)
is_valid = wave_size >= min_wave_size

// 3. Fibonacci 비율 검증
ratio = current_wave / previous_wave
is_fibonacci = (ratio >= 0.618 AND ratio <= 2.618)

// 4. Rule 검증
rule_valid = check_rules_1_to_7(waves)

// 5. 패턴 분류
pattern_type = classify_pattern(waves, ratios)
```

### 6.2 Diametric Formation 감지 알고리즘

```pinescript
// 1. 7개 파동 구조 확인
if waves.length() == 7:
    // 2. 상층 추세선: A-C-E-G 연결
    upper_line = fit_line(A, C, E, G)

    // 3. 하층 추세선: B-D-F 연결
    lower_line = fit_line(B, D, F)

    // 4. 교차점 계산
    intersection = find_intersection(upper_line, lower_line)

    // 5. Bow-Tie 수렴 확인
    if is_converging(upper_line, lower_line):
        return DIAMETRIC_FORMATION
```

### 6.3 Extracting Triangle 감지 알고리즘

```pinescript
// 1. 5-파동 ABC 구조
if waves.length() == 5:
    A = waves[0]
    B = waves[1]
    C = waves[2]
    D = waves[3]
    E = waves[4]

    // 2. 하강 비율 확인: A > C > E
    if A > C AND C > E:
        // 3. 상승 비율 확인: B < D
        if B < D:
            // 4. Wave-C > Wave-D 확인
            if C > D:
                // 5. Wave-D subdivisions 추적
                if count_subdivisions(D) > 3:
                    return EXTRACTING_TRIANGLE
```

---

## 7. 데이터 구조 정의

### 7.1 Wave 객체

```pinescript
type Wave
    int start_bar
    int end_bar
    float high
    float low
    float open
    float close
    float length
    string direction  // "up" or "down"
    int subdivisions
    float[] fibonacci_ratios
    string pattern_type  // "impulse", "flat", "zigzag", etc.
```

### 7.2 Pattern 객체

```pinescript
type Pattern
    Wave[] waves
    float[] ratios
    string type  // "diametric", "extracting", "neutral", etc.
    float confidence
    int formation_bars
    float[] trendlines
    string[] rules_passed
```

---

## 8. 신뢰성 평가 기준

### 8.1 패턴 신뢰성 스코어

```
Diametric Formation:
- 7-파동 정확도: 25%
- 추세선 수렴: 25%
- 비율 관계: 25%
- 시간대 검증: 25%
= 75%+ = HIGH CONFIDENCE

Extracting Triangle:
- 길이 비율 A>C>E: 30%
- 상승 B<D 관계: 30%
- C>D 규칙: 20%
- Subdivisions: 20%
= 80%+ = HIGH CONFIDENCE

Neutral Triangle:
- 수축 바이어스 확인: 40%
- 확장 바이어스 확인: 40%
- 방향성 부재: 20%
= 70%+ = MEDIUM CONFIDENCE
```

---

## 9. 성능 최적화

### 9.1 계산량 감소

```pinescript
// 1. 캐싱된 Wave 저장
cached_waves = array<Wave>(0)
update_cache(new_wave) // 최신 wave만 추가

// 2. 증분 계산
if new_bar():
    recalculate_last_3_waves()
    // 전체 재계산 대신 마지막 3개만

// 3. 조건부 검증
if major_wave_change:
    check_all_rules()
else:
    check_critical_rules_only()
```

---

## 10. 결론 및 권장사항

### 10.1 우선 구현 순서

1. **Phase 1 (1주):** Monowave + Neutrality 강화
2. **Phase 2 (2주):** Failure 패턴 + Extensions
3. **Phase 3 (3주):** Diametric + Extracting Triangle
4. **Phase 4 (4주):** 최적화 + 백테스트

### 10.2 예상 효과

```
- 거짓 신호 감소: 20-30%
- 패턴 정확도 향상: 25-35%
- 신규 패턴 적중률: 60-70% (초기)
```

### 10.3 주의사항

```
⚠ NEoWave 패턴은 매우 까다로움
⚠ 다중 시간대 검증 필수
⚠ 수동 확인 단계 권장
⚠ 백테스트 충분히 수행 필요
```

---

## 부록: 이미지 참고 목록

### NEoWaves 패턴 (15개)
- Logic (1): Diametric Formation 기본 구조
- Logic (2): Extracting Triangle 상세
- Logic (3): Neutral Triangle 수축/확장 바이어스
- Logic (4-5): Impulse 패턴 및 Fibonacci 레벨
- Logic (6): Spike High/Low
- Logic (7-8): Extracting Triangle 반복 및 특징
- Logic (9-10): 5th Failure Terminal
- Logic (11): Common Behavior 실수들
- Logic (12): NEoWave Patterns 실제 차트
- Logic (13): NEoWave Patterns Revealed (Neutral Triangle)
- Logic (14): Diametric Formation 실제 예시
- Logic (15): Extracting Formation 가격 스케일 예시

### Mastering Elliott Wave OCR-1 (99개)
- Logic (1-2): Monowave 정의 및 시간 단위
- Logic (3-7): Monowave 식별 및 차트 타입
- Logic (10): Rule of Neutrality 각도
- Logic (15): Rule 1 조건식별
- Logic (20): Rule 4 조건식별
- Logic (25): Rule 4b 상세
- Logic (30): Rule 7 활성화 요구사항
- Logic (35): Similarity & Balance Rules
- Logic (40): Structure Series 분류

### Mastering Elliott Wave OCR-2 (36개)
- Logic (100): Diagonal 패턴
- Logic (105): 5th Extension & Failure 패턴 (8가지)
- Logic (110): Double/Triple Zigzag
- Logic (115): Internal Relationships
- Logic (120): Flat 패턴 비율

---

**문서 작성:** 2026-01-21
**분석 이미지:** 150개
**분석 시간:** 약 2시간
**다음 단계:** PineScript 구현 시작
