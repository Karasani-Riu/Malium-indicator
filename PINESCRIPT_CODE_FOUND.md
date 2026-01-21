# Pine Script 코드 검색 결과 보고서

## 검색 대상
총 12개 레포지토리의 모든 MD 파일 분석

### 레포지토리 목록
1. `/tmp/analysis-repos/0Glenn-Neely-Mastering-Elliott-Wave/`
2. `/tmp/analysis-repos/1New-Patterns-Neely-Glenn-NEOWAVES/`
3. `/tmp/analysis-repos/2Robert-Balan-Elliott-Wave-Principles/`
4. `/tmp/analysis-repos/3Frost-Frechter_Elliott_Wave_Principle_Key_To_Market_Behavior/`
5. `/tmp/analysis-repos/4Encyclopedia-of-Chart-Pattern/`
6. `/tmp/analysis-repos/5Ian_Copsey_Harmonic_Elliott_Wave/`
7. `/tmp/analysis-repos/6Dow_Theory-7Wyckoff-Method/`
8. `/tmp/carney-repos/8-9-10Vol1-3-scoot-carney/`
9. `/tmp/carney-repos/11Three_Skills_of_Top_Trading/`
10. `/tmp/carney-repos/12Visual-Guide-to-Elliott-Wave-Trading/`
11. `/tmp/carney-repos/13Wiley_Trading_Thomas_N_Bulkowski_Encyclopedia_of_Chart_Patterns/`

---

## 검색 기준

다음 패턴들을 검색했습니다:

1. **코드 블록**: `\`\`\`pine`, `\`\`\`pinescript`
2. **Pine Script 버전 선언**: `//@version`
3. **함수 호출**: `indicator()`, `strategy()`
4. **기술분석 함수**: `ta.sma()`, `ta.crossover()` 등
5. **Pine Script 전용 문법**: `array.*`, `label.new()`, `var`, 조건문, 루프문

---

## 검색 결과

### 최종 결론: **실제 파인스크립트 코드 발견 0개**

모든 MD 파일들은 **기술 분석 관련 전자책의 OCR 변환본** 또는 **마크다운 형식의 이론 자료**로 구성되어 있습니다.

---

## 상세 분석

### 파일 구성
- **총 MD 파일 수**: 14개
- **대부분의 형태**: 전자책 본문의 OCR 변환본
- **컨텐츠 성격**:

#### 발견된 콘텐츠 유형
1. **Glenn Neely - Mastering Elliott Wave**
   - 주제: Elliott Wave 분석 이론
   - 형식: OCR 변환된 전자책
   - Pine Script 코드: 없음

2. **Encyclopedia of Chart Patterns**
   - 주제: 차트 패턴 분석 가이드
   - 형식: Thomas Bulkowski의 저서 디지털 버전
   - 크기: 3,653줄 (차트 패턴 설명 및 통계)
   - Pine Script 코드: 없음

3. **Wyckoff Method**
   - 주제: Wyckoff 분석 방법론
   - 형식: 마크다운 이론 설명서
   - 내용: Wyckoff 법칙, 공급/수요 분석, P&F 차트
   - Pine Script 코드: 없음

4. **Elliott Wave Trading (Gorman & Kennedy)**
   - 주제: Elliott Wave 거래 실전 예제
   - 형식: Bloomberg Press 출판본의 디지털 변환
   - 내용: 거래 사례 연구 및 기술적 분석
   - Pine Script 코드: 없음

5. **기타 파일들**
   - Scott Carney의 Harmonic Trading 관련 자료
   - Three Skills of Top Trading 교육 자료
   - 모두 이론적 설명 중심
   - Pine Script 코드: 없음

---

## 검색 세부 내용

### 검색 1단계: 코드 블록 패턴 검색
```bash
명령어: grep -r '```pine\|```pinescript' /tmp/analysis-repos /tmp/carney-repos --include="*.md"
결과: 매치 없음
```

### 검색 2단계: Pine Script 버전 선언 검색
```bash
명령어: grep -r '//@version' /tmp/analysis-repos /tmp/carney-repos --include="*.md"
결과: 매치 없음
```

### 검색 3단계: 함수 호출 패턴 검색
```bash
명령어: grep -r 'indicator(\|strategy(' /tmp/analysis-repos /tmp/carney-repos --include="*.md"
결과: 매치 없음 (기술 분석 이론 텍스트에서 일반적인 "indicator"와 "strategy" 단어만 검출)
```

### 검색 4단계: 코드 유사 패턴 검색
```bash
명령어: grep -r 'var \|if \|for \|while \|function ' (20줄 이상의 매치)
결과: 기술 분석 설명 텍스트만 발견, 실행 가능한 코드는 없음
```

---

## 결론 및 권장사항

### 현재 상황
- **12개 레포지토리에는 실제 실행 가능한 Pine Script 코드가 포함되어 있지 않습니다.**
- 모든 파일들은 기술 분석 교재 및 이론 설명 자료입니다.
- 이는 **자료의 성격상 당연한 결과**입니다 (차트 패턴, Elliott Wave, Wyckoff 방법론 등은 모두 개념적 분석 이론들).

### 실제 Pine Script 코드를 원하신다면

다음 리소스들을 확인하시기를 권장합니다:

1. **공식 Pine Script 문서**
   - https://www.tradingview.com/pine-script-docs/
   - indicator 및 strategy 샘플 코드

2. **TradingView Script Repository**
   - https://www.tradingview.com/scripts/
   - 사용자 작성 Pine Script 코드 및 인디케이터

3. **기술 분석 이론을 기반으로 한 Pine Script 구현**
   - Elliott Wave 인디케이터
   - Wyckoff Volume 인디케이터
   - Harmonic Pattern 스캐너
   - 등은 별도로 코딩해야 합니다.

---

## 부록: 발견된 MD 파일 목록

| 레포지토리 | 파일명 | 줄 수 |
|-----------|--------|------|
| 0Glenn-Neely-Mastering-Elliott-Wave | 0Glenn Neely - Mastering Elliott Wave-ocr-1.md | N/A |
| 1New-Patterns-Neely-Glenn-NEOWAVES | 1New Patterns Neely_Glenn_-_NEOWAVES.md | N/A |
| 2Robert-Balan-Elliott-Wave-Principles | 2Robert Balan Elliott Wave Principles-ocr-1.md | N/A |
| 3Frost-Frechter_Elliott_Wave_Principle | 3Frost&Frechter_Elliott_Wave_Principle_Key_To_Market_Behavior.md | 476 |
| 4Encyclopedia-of-Chart-Pattern | 4Encyclopedia-of-Chart-Pattern.md | 3,653 |
| 5Ian_Copsey_Harmonic_Elliott_Wave | 5Ian_Copsey_Harmonic_Elliott_Wave_The_Case_for_Modification_of_R.md | 249 |
| 6Dow_Theory-7Wyckoff-Method | 6George_W_Bishop_Dow_Theory_Appleton_Century.md | 816 |
| 6Dow_Theory-7Wyckoff-Method | 7Wyckoff-Method.md | 56 |
| 8-9-10Vol1-3-scoot-carney | 8vol1 scott carney.md | N/A |
| 8-9-10Vol1-3-scoot-carney | 9vol2 scott carney.md | N/A |
| 8-9-10Vol1-3-scoot-carney | 10vol3 scott carney.md | N/A |
| 11Three_Skills_of_Top_Trading | 11Three_Skills_of_Top_Trading.md | 688 |
| 12Visual-Guide-to-Elliott-Wave-Trading | 12Visual Guide to Elliott Wave Trading.md | N/A |
| 13Wiley_Trading_Thomas_N_Bulkowski_Encyclopedia_of_Chart_Patterns | 13Wiley_Trading_Thomas_N_Bulkowski_Encyclopedia_of_Chart_Patterns.md | 2,811 |

---

## 보고서 작성일
2026년 1월 21일

## 검색 환경
- 플랫폼: Linux 4.4.0
- 작업 디렉토리: /home/user/karasani
- 분석 대상: 12개 레포지토리 전체 MD 파일
- 총 검색 시간: 완료

---

**결과: 실제 실행 가능한 Pine Script 코드는 발견되지 않았습니다.**
