# 파인스크립트 코드 추출 및 분석 보고서

분석 대상: 7개 분석 레포지토리의 MD 파일들
작성일: 2026-01-21
현재 파일: `/home/user/karasani/advanced_market_analysis.pine` (2947줄)

---

## 1. 분석 레포지토리 목록

| # | 레포지토리명 | MD 파일 | 상태 | 주요 내용 |
|---|---|---|---|---|
| 0 | Glenn Neely - Mastering Elliott Wave | 12,843줄 | ✓ 분석 | 기본 Elliott Wave 이론 |
| 1 | NEoWaves (Glenn Neely) | 118줄 | ✓ 분석 | NEoWave 패턴 발견 |
| 2 | Robert Balan - Elliott Wave Principles | 3,517줄 | ✓ 분석 | 외환 시장 Elliott Wave |
| 3 | Frost-Prechter - Elliott Wave Principle | 8,281줄 | ✓ 분석 | 고전 Elliott Wave 이론 |
| 4 | Bulkowski - Chart Pattern Encyclopedia | 57,624줄 | ✓ 분석 | 75개 차트 패턴 통계 |
| 5 | Ian Copsey - Harmonic Elliott Wave | 3,739줄 | ✓ 분석 | 수정된 Harmonic Elliott Wave |
| 6 | Wyckoff Method + Dow Theory | 12,193줄 | ✓ 분석 | Wyckoff 5-Phase 방법론 |

**총 98,315줄 분석**

---

## 2. 현재 advanced_market_analysis.pine에 구현된 주요 기능

### A. Elliott Wave 패턴 (Lines 344-662)
- ✓ Fractal Elliott Waves (Major/Minor 구분)
- ✓ Impulse Waves (1-5)
- ✓ Corrective Waves (A-B-C)
- ✓ Connecting Waves (W-X-Y)
- ✓ Triangle Waves (A-B-C-D-E)
- ✓ Alternation Rules (Wave 2/4 분석)
- ✓ Elliott Wave Channeling
- ✓ Extension Relationships (Wave 1, 3, 5 분석)
- ✓ Truncated Wave 5 감지
- ✓ Diagonal Pattern 감지

### B. NEoWave 고급 패턴 (show_neowave_advanced)
- ✓ Diametric Formation (7-wave)
- ✓ Extracting Triangle (감지 로직 선언됨)
- ✓ Neutral Triangle (wave-c 가장 길음)
- ✓ 5th Failure Terminal (show_terminal_5th)

### C. Harmonic Pattern (Lines 1068-1580+)
- ✓ Gartley Pattern
- ✓ Butterfly Pattern
- ✓ Bat Pattern
- ✓ Crab Pattern
- ✓ Shark Pattern
- ✓ Cypher Pattern
- ✓ Deep Crab Pattern (Scott Carney)
- ✓ 5-0 Pattern

### D. Fibonacci 비율 상수 (Lines 117-146)
- ✓ 전통 Fibonacci 비율 (0.236 ~ 4.236)
- ✓ Ian Copsey Harmonic Ratios (0.414 ~ 4.236)

### E. Wyckoff 및 기타 패턴
- ✓ Wyckoff Phases (show_wyckoff)
- ✓ Dow Theory (show_dow)
- ✓ Kondratiev Wave (250 bars lookback)
- ✓ Deep Depth Cycle
- ✓ Livermore Accumulation Cylinder

### F. Chart Patterns (Lines 35-40)
- ✓ Head & Shoulders
- ✓ Double Top/Bottom
- ✓ Cup with Handle
- ✓ Rectangle Patterns
- ✓ Diamond Patterns

---

## 3. 각 MD 파일에서 새로운 알고리즘 추출

### 3-1. NEoWaves (Glenn Neely) - 1New Patterns Neely_Glenn_-_NEOWAVES.md

**이미 구현된 내용:**
- Diametric Formation
- Extracting Triangle
- Neutral Triangle
- 5th Failure Terminal

**새로운 발견 패턴들:**

#### Diametric Formation (7-wave 패턴)
```
패턴 규칙:
- Wave E > Wave D (핵심 특성)
- 7개 파동으로 구성
- 기존 Contracting Triangle과 다른 특성

감지 로직:
1. 5개 이상의 연속 파동 감지
2. 파동 크기 비교: E > D 확인
3. 패턴 방향 결정 (상승/하강)
4. 시간 요소 검토 (Wave E가 빠르게 빠져나와야 함)
```

#### Extracting Triangle 특성
```
핵심 감지 규칙:
1. Wave-D는 항상 Wave-C보다 큼
2. 각 연속 하락이 더 작은 가격으로 → 상승 저점
3. 각 연속 반등이 더 큰 가격으로 → 상승 고점
4. Wave-B의 시간이 Wave-A, C보다 짧음
5. Breakout이 느림 (Contracting Triangle과 다름)
```

#### Neutral Triangle (Wave-C가 가장 김)
```
특성:
- 3rd Wave Extension Impulse와 유사
- Wave-C가 가장 긴 파동
- 균형 잡힌 행동 (even distribution)
- 가격과 시간 변화가 일정
```

#### 5th Failure Terminal
```
특성:
- Wave-2와 4가 겹침 (중요!)
- 내부 구조가 Corrective (Impulsive 아님)
- Wave 2 & 4의 극단적 크기 차이
- 식별이 어려움 (종료 후에야 인식)

확인 신호:
- Wave-1과 3이 일반적 임펄스 구조
- Wave-2와 4의 심각한 교차
- 극단적인 Alternation
```

---

### 3-2. Ian Copsey - Harmonic Elliott Wave (5Ian_Copsey_Harmonic_Elliott_Wave_...)

**핵심 발견: 수정된 Elliott Wave 이론**

**이미 구현된 내용:**
- Ian Copsey 비율들 (FIB_0414 ~ FIB_4236)
- Harmonic Patterns (Gartley, Butterfly 등)

**새로운 알고리즘:**

#### Modified Impulsive Wave Structure
```
Copsey의 핵심 수정 사항:
1. 표준 Fibonacci 비율이 자주 실패 (50% 미만 성공률)
2. Wave 3가 자주 예상보다 일찍 종료
3. 상하위 파동도 Fibonacci 관계를 따라야 함

적용 로직:
- 모든 파동 간 Fibonacci/Harmonic 비율 확인
- 하위 파동의 투영이 상위 파동과 조화를 이루어야 함
- Multiple potential targets 대신 Harmonic alignment 우선
```

#### Derivative Ratios (파생 비율)
```
표준 Fibonacci 외에 추가 비율:
- Wave relationships 간의 파생 비율 사용
- 표준 Fib 비율 실패 시 대체
- Momentum 기반 확인

예:
- Wave(A) = 1.0
- Wave(B) = 0.618 * Wave(A)
- Wave(C) = 1.618 * Wave(A)
→ 이들이 harmonious 구조 형성
```

#### Wave Equality vs Extension 판별
```
문제: 언제 Wave 1 = Wave 5인가? 언제 Extension인가?

Copsey 접근법:
1. 모든 가능한 projection targets 계산
2. 하위 파동의 구조와 비교
3. Multiple degree wave relationships 확인
4. 가장 Harmonic한 target 선택

구현:
f_copsey_wave_equality(wave1, wave3, wave5, lower_waves) =>
    // 모든 가능한 비율 조합 계산
    // Harmonic 정렬도 계산
    // 가장 확률 높은 target 반환
```

---

### 3-3. Wyckoff Method (7Wyckoff-Method.md)

**이미 구현된 내용:**
- show_wyckoff 토글

**새로운 감지 알고리즘:**

#### Wyckoff 5-Phase Accumulation/Distribution

```pinescript
// Phase A: Stopping of Prior Trend
// PS (Preliminary Support/Supply)
// SC (Selling Climax) / BC (Buying Climax)
// AR (Automatic Rally/Reaction)
// ST (Secondary Test)

// Phase B: Building Cause
// Spring (들어올린 후 내려옴) / Shakeout (역방향)
// Multiple tests of supply/demand

// Phase C: Testing Supply/Demand
// Spring or Shakeout 형성
// Low volume = 준비 완료 신호

// Phase D: Markup/Markdown
// SOS (Sign of Strength) 또는 SOW (Sign of Weakness)
// Higher lows or Lower highs

// Phase E: Exit Phase
// Trend 명확함
// Re-accumulation TRs 가능
```

#### 9 Buying Tests (Accumulation)
```
1. 다운사이드 Price Objective 달성 (P&F)
2. PS, SC, ST 형성 (Bar & P&F)
3. 활동성 강세 (반등 시 volume ↑, 하락 시 ↓)
4. Downward stride 돌파
5. Higher lows 형성
6. Higher highs 형성
7. Stock 시장보다 강함
8. Base forming (수평선)
9. 예상 상승 = 최소 3 × 손실 위험

구현 로직:
f_wyckoff_buying_tests() =>
    test1 = f_pf_downside_objective()
    test2 = f_detect_ps_sc_st()
    test3 = f_bullish_activity()
    test4 = f_downtrend_broken()
    test5 = f_higher_lows()
    test6 = f_higher_highs()
    test7 = f_relative_strength()
    test8 = f_base_forming()
    test9 = f_reward_risk_ratio()
```

#### 9 Selling Tests (Distribution)
```
동일 로직이지만 역방향:
1. 업사이드 Price Objective 달성
2. PSY, BC, ST 형성
3. 활동성 약세 (반등 시 volume ↓, 하락 시 ↑)
4. Upward stride 돌파
5. Lower highs 형성
6. Lower lows 형성
7. Stock 시장보다 약함
8. Crown forming
9. 예상 하락 = 최소 3 × 손실 위험
```

#### Wyckoff Cause & Effect (P&F Count)
```
로직:
1. Trading Range의 "Cause" = 수평 P&F count
2. TR을 빠져나간 후의 "Effect" = count 높이만큼 이동

구현:
- Horizontal P&F count 계산
- 가장 보수적인 count부터 시작
- 목표 가격 = TR의 하단 + count 높이
- 또는 목표 가격 = (TR 상단 + 하단) / 2 + count 높이
```

#### Effort vs Result (Volume/Price Divergence)
```
신호:
1. Wide spread + High volume + Price barely moves (Bearish)
   → 공급이 많음 = 약세
2. Narrow spread + High volume + Price barely moves (Bullish in TR)
   → 수요가 많음 = 강세 (공급 흡수)
3. Wide spread + High volume + Strong price move
   → Harmonic (강강/약약) = 추세 확인

구현:
f_effort_vs_result(bar_num) =>
    spread = high - low
    volume_sma = ta.sma(volume, 20)
    volume_normalized = volume / volume_sma
    price_change = close - close[1]

    effort_score = spread * volume_normalized
    result_score = math.abs(price_change)

    divergence = effort_score / (result_score + 0.0001)

    // divergence > threshold = price-volume divergence
```

---

### 3-4. Bulkowski - Chart Pattern Encyclopedia (4Encyclopedia-of-Chart-Pattern.md)

**이미 구현된 내용:**
- Head & Shoulders
- Double Top/Bottom
- Cup with Handle
- Rectangle
- Diamond

**새로운 차트 패턴들 (75개 중 미구현):**

#### High-Success Chart Patterns (통계 기반)

```
1. Bump-and-Run Reversal (Bottom)
   성공률: 55% (최고 성능!)
   평균 상승: 높음
   적용:
   - 급상승 후 확인 → 되돌림
   - 새로운 상승 시작 전에 확인

2. Broadening Formations
   - Ascending (우상향)
   - Descending (우하향)
   - Right-angled
   적용: Reversal 신호

3. Flags & Pennants (High-Tight Flags)
   성공률: 높음 (60%+)
   지속 패턴 (Continuation)

4. Island Reversals
   적용: V-recovery 또는 V-decline

5. Measured Move (Up/Down)
   적용: Extension target 계산
```

#### 패턴별 통계 데이터
```
Bulkowski 통계 포함:
- Average Rise/Decline (평균 수익률)
- Success/Failure Rates
- Busted Pattern Performance
- Volume Trend Analysis
- Pattern Height/Width Statistics
- Days to Ultimate High/Low
- Post-breakout Pullback Rates

구현 로직:
f_chart_pattern_success_rate(pattern_type) =>
    // Bulkowski 통계에 기반한 필터링
    // pattern_type별 success probability 반환
    // Risk/reward ratio 계산
```

#### Pattern Recognition 개선사항
```
현재: 기본적인 패턴 형태만 감지
개선: Bulkowski 통계 기반 필터링 추가

f_filter_high_success_patterns() =>
    // 1. 패턴 형태 확인
    // 2. Historical success rate 확인
    // 3. Volume 패턴 확인
    // 4. Pattern size 적절성 확인
    // 5. Market condition matching (Bull/Bear)
```

---

### 3-5. Frost-Prechter - Elliott Wave Principle (3Frost&Frechter...)

**이미 구현된 내용:**
- 기본 Elliott Wave 이론 (거의 모두)
- Impulse/Corrective waves
- Truncation (5T)
- Diagonal patterns
- Fibonacci ratios

**새로운 개념:**

#### Orthodox Tops and Bottoms
```
개념: Elliott Wave 패턴이 정상적으로 끝나는 지점

적용:
- Wave 5가 wave 3의 상단을 넘지 못함 (Truncation)
- Wave C가 wave A의 하단을 넘지 못함 (약한 조정)

감지:
f_detect_orthodox_bottom() =>
    // Wave 5 < Wave 3 high 확인
    // 이것이 orthodox bottom이 되어야 함
```

#### Channeling & Throwover
```
Channeling: Parallel channel 내에서 impulse wave 움직임
Throwover: Channel 경계를 넘는 move

적용:
- Wave 5 target = channel 상단 또는 그 근처
- Throwover = 강한 momentum 신호
```

#### Wave Personality
```
Wave 특성:
1. Wave 1: 약간의 거래량, 참가자 부족
2. Wave 2: 거의 완전한 되돌림
3. Wave 3: 가장 강한 wave, 가장 활동적, 가장 길음
4. Wave 4: 복잡한 형태, 파동 내 조정
5. Wave 5: Wave 1보다 약할 수 있음, 끝에서 거래량 ↓

A wave: 약한 참여 (아직 모두가 확신하지 않음)
B wave: 혼합된 신호 (혼란스러운 파동)
C wave: 강한 참여 (모두가 아래로 간다고 확신)
```

---

### 3-6. Robert Balan - Elliott Wave Principles (2Robert Balan...)

**이미 구현된 내용:**
- 기본 Elliott Wave (Forex 적용)

**새로운 개념:**

#### Flat Correction vs Horizontal Triangle
```
Flat: 3-wave (A-B-C) - 가장 흔한 조정

특성:
- Wave B ≈ 100-125% of Wave A
- Wave C ≈ 100% of Wave A
- 상대적으로 빠른 move

Horizontal Triangle: 5-wave consolidation
- 각 wave가 감소하는 크기
- ABCDE pattern
- 느린 move
```

#### Pattern Combinations (WXY)
```
Double Three (WXY):
- W (1st three) + X (connector) + Y (2nd three)
- 복잡한 조정

Triple Three (WXYXZ):
- 추가 connector + 3rd three
- 매우 복잡한 조정

감지:
f_detect_wxyz_combination() =>
    // W 부분 감지
    // X (connector) 감지 - 항상 반대 방향
    // Y 부분 감지
    // Optional Z 부분
```

---

## 4. 현재 advanced_market_analysis.pine에 부족한 새로운 함수/알고리즘

### 높은 우선순위 추가 함수

#### 1. Wyckoff Phase 감지 강화
```pinescript
f_detect_wyckoff_phase_a() =>
    // PS, SC, AR, ST 모두 감지
    // Accumulation vs Distribution 구분

f_detect_spring_shakeout() =>
    // Spring: Support 아래 가서 되돌림
    // Shakeout: Resistance 위로 가서 되돌림
    // Low volume 확인

f_detect_wyckoff_events() =>
    // SOS (Sign of Strength)
    // SOW (Sign of Weakness)
    // LPS (Last Point of Support)
    // LPSY (Last Point of Supply)
    // BU (Back-up)
```

#### 2. Effort vs Result 감지
```pinescript
f_effort_vs_result() =>
    // Volume 대비 price change 분석
    // 조화(harmony) 또는 분기(divergence) 감지
    // Bullish/Bearish 신호 생성
```

#### 3. NEoWave 패턴 감지 강화
```pinescript
f_detect_diametric_formation() =>
    // 7-wave 패턴
    // Wave E > Wave D 확인
    // 방향 판단

f_detect_neutral_triangle() =>
    // Wave C 가장 김
    // Even distribution 확인

f_detect_extracting_triangle() =>
    // Wave D > Wave C (항상)
    // 각 하락이 더 작은 저점
    // 각 반등이 더 큰 고점

f_detect_5th_failure_terminal() =>
    // Wave 2와 4의 겹침
    // Internal structure가 corrective
    // 극단적 alternation
```

#### 4. Copsey의 Harmonic Alignment 확인
```pinescript
f_check_harmonic_alignment(wave_levels) =>
    // 여러 파동 간 Fibonacci 비율 확인
    // 하위 파동이 상위 파동과 조화로운지 확인
    // Harmonic score 계산

f_find_harmonic_targets(wave_a, wave_b) =>
    // 표준 비율이 아닌 Harmonic 비율 적용
    // 더 정확한 target 계산
```

#### 5. Bulkowski 차트 패턴 강화
```pinescript
f_detect_bump_and_run() =>
    // Steep uptrend 후 pullback
    // 새로운 상승 전의 재확인

f_detect_island_reversal() =>
    // Gap + Consolidation + Gap (반대)
    // V-recovery 또는 V-decline

f_detect_broadening_formations() =>
    // Ascending, Descending, Right-angled
    // Reversal 패턴

f_chart_pattern_filters() =>
    // Bulkowski 통계 적용
    // Success rate 기반 필터링
```

#### 6. Wave Personality & Characteristics
```pinescript
f_wave_personality(wave_number, wave_type) =>
    // Wave 1: 약한 특성 (가능한 시작)
    // Wave 3: 강한 특성 (가장 강함)
    // Wave 5: 약할 수 있음 (끝 근처)

    // Volume, momentum, complexity 분석
```

#### 7. Wyckoff P&F Count
```pinescript
f_calculate_pf_count(trading_range_start, trading_range_end) =>
    // Point & Figure 수평 count 계산
    // Price objective = count height + TR low
    // 보수적/공격적 count 옵션
```

---

## 5. 새로운 기능별 구현 난이도 평가

| 기능 | 난이도 | 예상 코드양 | 우선순위 |
|---|---|---|---|
| Wyckoff Phase 감지 | 중 | 200-300줄 | 높음 |
| Effort vs Result | 낮 | 50-100줄 | 높음 |
| NEoWave 강화 | 중 | 150-200줄 | 중간 |
| Harmonic Alignment | 높음 | 300-400줄 | 중간 |
| Chart Pattern 통계 필터 | 높음 | 200-300줄 | 중간 |
| Copysey Ratios 적용 | 높음 | 250-350줄 | 낮음 |
| P&F Count | 중 | 100-150줄 | 낮음 |

---

## 6. 파인스크립트에 없는 파일 정보

### 모든 MD 파일이 코드 블록 없음
- 모든 7개 레포지토리의 MD 파일이 **파인스크립트 코드를 포함하지 않음**
- 모두 이론, 설명, 다이어그램 설명 형식
- **사용자가 직접 작성한 가능성 없음**

### 패턴 이론은 풍부
- 각 이론의 세부 규칙과 특성 명확
- 차트 패턴의 통계 데이터 풍부
- 새로운 알고리즘 개발에 충분한 기초

---

## 7. 추천 구현 순서

### Phase 1 (즉시): 높은 수익 패턴
1. Bump-and-Run Reversal (55% 성공률)
2. Wyckoff Spring/Shakeout 감지
3. Effort vs Result divergence

### Phase 2 (단기): 신뢰성 개선
4. NEoWave 패턴 강화 (Diametric, Extracting)
5. Wyckoff Phase A-E 완전 구현
6. Wave Personality 기반 필터링

### Phase 3 (중기): 고급 기능
7. Harmonic Alignment 확인
8. Bulkowski 통계 필터링
9. Copsey의 Modified Wave 비율

---

## 8. 세부 코드 예제

### A. Wyckoff Spring 감지
```pinescript
f_detect_spring() =>
    // Trading Range의 하단 아래로 내려가서
    // 같은 날짜나 다음 날짜에 TR 위로 복구

    size = array.size(zz_price)
    if size >= 3
        p_prev = array.get(zz_price, size - 3)
        p_bottom = array.get(zz_price, size - 2)
        p_current = array.get(zz_price, size - 1)

        tr_bottom = math.min(p_prev, p_bottom)
        is_spring = p_bottom < tr_bottom and p_current > tr_bottom

        if is_spring
            current_volume = volume
            volume_20 = ta.sma(volume, 20)
            is_low_volume = current_volume < volume_20 * 1.2

            if is_low_volume
                label.new(bar_index, p_bottom,
                    "Spring\n(Buy Signal)",
                    style=label.style_label_center,
                    color=color.green, textcolor=color.white)
```

### B. Effort vs Result
```pinescript
f_effort_vs_result() =>
    spread = high - low
    volume_ma = ta.sma(volume, 20)
    volume_ratio = volume / volume_ma
    price_move = close - open

    effort = spread * volume_ratio
    result = math.abs(price_move)
    ratio = effort / (result + 0.0001)

    // ratio > 1.5 = 가격 상승하지 않음 (약세 신호)
    // ratio < 0.5 = 큰 가격 움직임 (강세 신호)
    ratio
```

### C. NEoWave Extracting Triangle 감지
```pinescript
f_detect_extracting_triangle() =>
    size = array.size(zz_price)
    if size >= 5
        p1 = array.get(zz_price, size - 5)  // A
        p2 = array.get(zz_price, size - 4)  // B
        p3 = array.get(zz_price, size - 3)  // C
        p4 = array.get(zz_price, size - 2)  // D
        p5 = array.get(zz_price, size - 1)  // E

        wave_c = math.abs(p3 - p2)
        wave_d = math.abs(p4 - p3)

        // 핵심: Wave D > Wave C
        is_extracting = wave_d > wave_c

        if is_extracting
            // 추가 확인: 하락/반등 패턴
            label.new(bar_index, p5,
                "Extracting △",
                style=label.style_label_center,
                color=color.purple)
```

---

## 9. 결론 및 권장사항

### 현재 상태
- **매우 포괄적인 Elliott Wave 구현** ✓
- **Harmonic Pattern 완전 구현** ✓
- **기본 Chart Pattern 구현** ✓
- **Wyckoff 기초 구현** △ (5-Phase, 9 Tests 미흡)
- **NEoWave 기초 선언** △ (감지 로직 불완전)

### 즉시 추가 권장
1. **Wyckoff Event 감지** (Spring, Shakeout, SOS, SOW)
2. **Effort vs Result 다이버전스**
3. **NEoWave Extracting Triangle** 정확한 감지

### 장기 개선 사항
1. Bulkowski 통계 데이터 기반 필터링
2. Ian Copsey의 Harmonic 비율 최적화
3. 교차 마켓 패턴 검증

---

**분석 완료**
마지막 수정: 2026-01-21
