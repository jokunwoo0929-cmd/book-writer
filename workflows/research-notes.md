# SMPS 조사 노트

> 작성일: 2026-10-24
> 작성자: researcher
> 목적: writer가 사실에 근거한 초고를 작성할 수 있도록 챕터별 핵심 자료와 출처를 정리한다.

---

## 챕터 1 조사 결과 - 2026-10-24

### 이 조사의 목적
독자(비전공자)에게 신뢰할 수 있는 근거를 제공하기 위해(Why) 공신력 있는 기술 문서와 전문 사이트에서 LPS·SMPS 비교 수치, 발열 원인, 전압 규격 자료를 수집한다(What).

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| LPS vs SMPS 효율 비교 | LPS: 20~50%, SMPS: 65~95% (일반적으로 80~90% 달성 가능) | k-rnd.com, tutorialspoint.com | 높음 |
| 충전기 발열의 물리적 이유 | AC→DC 변환 과정에서 트랜지스터·다이오드·콘덴서 등 내부 부품의 저항으로 전력 일부가 열로 변환됨. 선형 방식은 잉여 전압을 저항으로 소모하므로 발열이 SMPS보다 훨씬 큼 | it.rushmac.net, a-ha.io | 높음 |
| 한국 콘센트 규격 | 220V, 60Hz, Type C(유로플러그)·Type F(슈코) 사용. 1973~2005년 110V→220V 승압 사업 완료 | agoda.com, epnc.co.kr | 높음 |
| 주요 기기 요구 전압 | 스마트폰: DC 5V(USB), 노트북: DC 19~20V, LED 조명: DC 12V 또는 24V | namu.wiki, digi-royal.com, ledyilighting.com | 높음 |

### 추가 참고 자료

- 출처: [SMPS란? SMPS 회로 설계 - k-rnd.com](https://k-rnd.com/smps란-smps-회로-설계/)
  - 요약: SMPS와 선형 전원공급장치의 효율, 크기, 노이즈 특성을 비교 설명. 선형 20~50% vs SMPS 65~95% 수치 확인.

- 출처: [선형 전압 조정기 대 스위칭 조정기 - Digi-Key Forum](https://forum.digikey.com/t/topic/15511)
  - 요약: 선형 조정기와 스위칭 조정기의 효율·잡음·응용 분야 비교. 400W 이하는 LPS, 이상은 SMPS가 비용 효율적.

- 출처: [충전기가 뜨거워지는 이유 - IT정보 개발자Life](https://it.rushmac.net/1567)
  - 요약: AC→DC 변환 시 에너지 손실이 열로 방출되는 원리. 고속 충전 시 더 많은 열 발생.

- 출처: [한국의 콘센트 종류, 전압, 플러그 호환성 - Agoda](https://www.agoda.com/ko-kr/travel-guides/south-korea/electric-socket-types-voltage-and-plug-compatibility-in-south-korea/)
  - 요약: 한국 220V/60Hz 규격, 콘센트 타입(C, F형) 설명.

- 출처: [220V 콘센트를 사용하는 한국과 중국 - 테크월드(EPNC)](https://www.epnc.co.kr/news/articleView.html?idxno=82492)
  - 요약: 한국 220V 승압 배경 및 콘센트 형식 차이 설명.

### writer 전달 사항

- 강조할 내용:
  - LPS 효율(20~50%) 대비 SMPS 효율(65~95%)은 비전공자가 직관적으로 이해할 수 있는 핵심 수치. "전기 100을 넣으면 최대 50만 유용하게 쓰고 나머지는 열로 낭비된다" 식의 비유 활용 권장.
  - 한국 콘센트 220V와 스마트폰 5V, 노트북 19V의 전압 차이를 예시로 들어 전압 변환의 필요성을 설명할 것.
  - 충전기 발열은 독자가 일상에서 직접 경험하는 현상이므로 도입부 사례로 활용 가능.
- 주의 사항 (불확실한 정보):
  - LPS 효율 하한값(20%)은 출처마다 30~40%로 상이한 경우 있음. 보수적으로 "20~50%" 범위를 사용하되, 조건에 따라 편차가 크다고 병기 권장.

---

## 챕터 2 조사 결과 - 2026-10-24

### 이 조사의 목적
독자가 SMPS 내부 동작 원리를 이해할 수 있도록(Why) 스위칭 주파수 수치, 핵심 부품 역할, PWM 개념을 비유 중심으로 정리한다(What).

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| SMPS 스위칭 주파수 범위 | 일반적으로 20kHz~1MHz. 소비자용 제품(ATX 전원, 어댑터 등)은 50~500kHz 범위가 전형적. 저주파 SMPS는 20~100kHz, 고주파는 MHz 영역까지 가능 | lcsc.com, elexana.com, sciencedirect.com | 높음 |
| 트랜스포머 역할 | 전자기 유도 원리를 이용해 전압을 변환(올리거나 낮춤). SMPS에서는 고주파 신호를 사용하므로 철심 없이도 소형으로 제작 가능 | cafe.daum.net(funny-circuit), wiki.homerecz.com | 높음 |
| 다이오드 역할 | 교류(AC)를 한 방향으로만 통과시켜 직류(DC)에 가까운 파형으로 정류(정류 역할). 전류가 역방향으로 흐르는 것을 차단하는 "일방통행 밸브" | cafe.daum.net(funny-circuit) | 높음 |
| 캐패시터 역할 | 정류 후 남아 있는 교류 성분(리플)을 흡수·저장하여 평탄한 직류 출력으로 다듬는 평활 역할. "전기 저수지"에 비유 가능 | cafe.daum.net(funny-circuit) | 높음 |
| PWM 개념 | 펄스가 켜져 있는 시간 비율(듀티 사이클)을 조절해 평균 전압을 제어. 듀티 사이클이 높을수록 평균 전압 상승 | digikey.kr, ktword.co.kr, namu.wiki | 높음 |

### 추가 참고 자료

- 출처: [SMPS Design: Switching Power Supply Circuits - smps.us](https://www.smps.us/smpsdesign.html)
  - 요약: SMPS 설계 전반에 관한 기술 자료. 스위칭 주파수와 EMI 간의 관계 포함.

- 출처: [Switched-Mode Power Supply - LCSC Blog](https://www.lcsc.com/blog/switched-mode-power-supply/)
  - 요약: SMPS 완전 설계 가이드. 동작 원리, 주파수 범위, 구성 부품 설명.

- 출처: [펄스 폭 변조란 무엇이고 어떻게 사용되는가 - Digi-Key KR](https://www.digikey.kr/ko/blog/pulse-width-modulation)
  - 요약: PWM 개념, 듀티 사이클, 컴퓨터 팬(Fan) 속도 제어 응용 사례 포함.

- 출처: [PWM Pulse Width Modulation 펄스 폭 변조 - 정보통신기술용어해설](http://www.ktword.co.kr/test/view/view.php?no=5517)
  - 요약: PWM 정의, ON/OFF 시간 비율 변조 원리 설명.

- 출처: [전원회로 정류·평활회로 - 재미있는 전자공작소(Daum 카페)](https://m.cafe.daum.net/funny-circuit/M4Cw/79)
  - 요약: 트랜스포머·다이오드·캐패시터의 AC→DC 변환 역할 순서 설명.

- 출처: [EMF Testing, EMI Diagnostics - Elexana](https://www.elexana.com/switch-mode-power-supplies-frequencies-emc-compliance-and-mitigation-techniques)
  - 요약: SMPS 스위칭 주파수와 EMC 준수 관계. 일반적 주파수 범위(10kHz~수 MHz) 언급.

### writer 전달 사항

- 강조할 내용:
  - PWM 비유: "선풍기 버튼을 빠르게 켰다 껐다 반복하면 실제로는 중간 세기처럼 느껴지는 것과 같은 원리"로 설명 권장.
  - 트랜스포머는 "학교 앞 횡단보도 신호등" 대신 "물 파이프 단면적 변환기(압력=전압, 유량=전류)" 비유도 효과적.
  - 스위칭 주파수(예: 100kHz)가 가청 주파수(20Hz~20kHz)보다 높아 우리 귀에 들리지 않는다는 점을 언급하면 독자 관심 유도 가능.
- 주의 사항 (불확실한 정보):
  - 스위칭 주파수 상한은 기술 발전에 따라 변동이 크며, MHz 영역까지 확장되는 추세. "일반 소비자용은 수십~수백 kHz"로 범위를 한정하여 서술하는 것이 안전.

---

## 챕터 3 조사 결과 - 2026-10-24

### 이 조사의 목적
독자가 SMPS의 실생활 연관성과 안전 규격의 필요성을 이해할 수 있도록(Why) 응용 제품 사례, EMI 발생 원인, KC·UL·CE 인증 개요를 정리한다(What).

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| SMPS 주요 응용 분야 | 스마트폰 충전기, 노트북 어댑터, LED 조명 전원, TV·셋톱박스 내장 전원, PC 파워서플라이(ATX), 의료기기 전원 등 | namu.wiki(SMPS), lcsc.com | 높음 |
| EMI 발생 원인 | SMPS 내부 스위칭 소자(MOSFET, IGBT 등)의 고속 ON/OFF 동작으로 빠르게 변화하는 전압·전류가 발생. 이 변화가 도선 주변에 전자기장을 형성하여 인근 기기 오동작 유발. 전도성 EMI(배선 경유)와 방사성 EMI(공중 방사) 두 종류 존재 | elementkorea.kr, daily-note.kr | 높음 |
| EMC 인증 개요 | EMC(전자기 적합성)는 제품이 전자파를 과도하게 방출하지 않고 외부 전자파에서도 정상 동작하는지 평가. CISPR(IEC 산하)가 국제 표준 제정 | elementkorea.kr, nemko.com | 높음 |
| KC 전기용품안전인증 | 한국 내 판매되는 전기용품 필수 인증. 안전인증·안전확인·공급자적합성확인 3단계로 구분. 제품 시험 + 공장심사 방식 | kcl.re.kr, kcrlab.co.kr | 높음 |
| UL 인증 (미국) | 미국 Underwriters Laboratories 발급. 북미 시장 판매 필수. 제3자 독립 시험기관이 평가. 대부분의 미국 주에서 판매 요건 | misumi-ec.com, ufinebattery.com | 높음 |
| CE 마킹 (유럽) | 유럽 경제 지역(EEA) 판매 의무 표시. "Conformité Européenne" 약자. UL과 달리 제조사 자체 선언 방식(제3자 인증 불필요) | misumi-ec.com, tonful.com | 높음 |

### 추가 참고 자료

- 출처: [SMPS - 나무위키](https://namu.wiki/w/SMPS)
  - 요약: SMPS 응용 분야, 구성, 장단점을 한국어로 종합 정리.

- 출처: [EMC와 EMI의 차이점 - Nemko](https://www.nemko.com/ko/blog/emc-vs-emi-whats-the-difference)
  - 요약: EMI(방출)와 EMS(내성)의 차이, EMC 개념 정의.

- 출처: [전자파 장해 시험 EMI 완벽 가이드 - Element Korea](https://elementkorea.kr/전자파-장해-시험-emi에-대한-완벽-가이드/)
  - 요약: EMI 시험 항목, 전도성/방사성 EMI 설명.

- 출처: [KC vs CE vs UL 비교: 글로벌 인증 선택 전략 완벽 가이드 - UFine Battery](https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/)
  - 요약: KC, CE, UL 세 인증의 적용 지역, 방식, 비교 정리.

- 출처: [안전 규격에 대하여 - 미스미](https://kr.misumi-ec.com/tech-info/categories/technical_data/td01/a0003.html)
  - 요약: UL, CE, KC 등 주요 국제 안전 규격 개요 및 차이점 설명.

- 출처: [KC 전기안전 - KCR Lab](https://www.kcrlab.co.kr/kc_safety/)
  - 요약: KC 전기용품안전인증 신청 절차 및 제출 서류.

### writer 전달 사항

- 강조할 내용:
  - 독자 주변에 SMPS가 들어 있는 제품(스마트폰 충전기, 노트북 어댑터, LED 조명)을 먼저 나열하여 "이미 SMPS를 매일 사용하고 있다"는 친근감을 형성.
  - EMI를 "음악 재생 중 전자레인지를 켰더니 라디오에 잡음이 생기는 것"과 같은 일상 경험에 비유하면 비전공자 이해도 향상.
  - KC, UL, CE 인증마크는 독자가 제품 구매 시 직접 확인할 수 있는 표시이므로 "충전기 뒷면에 붙어 있는 마크"를 예시로 활용 권장.
- 주의 사항 (불확실한 정보):
  - CE 마킹이 "제조사 자체 선언"이라는 점은 일부 소비자에게 혼란을 줄 수 있음. "유럽 기준을 충족했다는 선언"이라고 간략히 표현하고 세부 절차는 생략 권장.
  - KC 인증 세부 품목 분류(안전인증·안전확인 구분)는 제품 종류에 따라 달라지므로 writer는 일반적 설명 수준으로만 서술할 것.

---

## 전체 조사 요약

| 챕터 | 핵심 수치/개념 | 조사 완료 여부 |
|---|---|---|
| 챕터 1 | LPS 효율 20~50%, SMPS 효율 65~95%, 한국 220V/60Hz, 스마트폰 5V·노트북 19V | 완료 |
| 챕터 2 | 스위칭 주파수 20kHz~1MHz(소비자용 50~500kHz), 트랜스포머·다이오드·캐패시터 역할, PWM 듀티 사이클 | 완료 |
| 챕터 3 | SMPS 응용 5가지, EMI 전도성·방사성 구분, KC·UL·CE 인증 개요 | 완료 |

---

## [2차 조사] 챕터 1: 전원공급장치란 무엇인가 조사 결과 - 2026-10-24

### 이 조사의 목적
독자(대학교 1~2학년생)가 교류/직류 개념과 전원 변환의 필요성을 직관적으로 이해할 수 있도록, 비유 사례와 신뢰할 수 있는 수치 자료를 1,500자 분량 집필 기준으로 보강한다.

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| AC/DC 차이 — 비유 | 직류(DC)는 "한쪽으로만 흐르는 강물", 교류(AC)는 "앞뒤로 반복되는 파도" | https://www.pangyimush.com/dc-vs-ac/ | 높음 |
| AC/DC 차이 — 원리 | 직류는 전자가 한 방향으로 이동. 교류는 전자 방향이 주기적으로 반전(한국 60Hz = 초당 60회 반전) | https://www.a-ha.io/questions/418e8e2717e29764bd0b51cfa52ef294 | 높음 |
| 한국 콘센트 규격 | AC 220V, 60Hz. 한국전력 공식 규격 | https://cyber.kepco.co.kr/sk//app/newsletter/209/detail_02.html | 높음 |
| 주요 기기 요구 전압 | 스마트폰 충전기 출력: DC 5~9V / 노트북 어댑터: DC 19~20V / LED 스트립: DC 12V 또는 24V | https://www.asus.com/kr/support/faq/1015066/ , https://ledyilighting.com/ko/led-strip-light-internal-schematic-and-voltage-information/ | 높음 |
| LPS 효율 [미확인-하한] | 30~60% (출처마다 편차: 일부 출처 40~60%, 다른 출처 30~40%) | https://www.tutorialspoint.com/article/difference-between-smps-and-linear-power-supply , https://www.wevolver.com/article/linear-vs-switching-power-supply | 중간 (하한 편차 주의) |
| SMPS 효율 | 65~95% (일반적 범위). 고품질 제품은 최대 95%까지 | https://www.tutorialspoint.com/article/difference-between-smps-and-linear-power-supply , https://electronicscoach.com/difference-between-linear-supply-and-switch-mode-power-supply.html | 높음 |
| 발열 원인 — LPS | 선형 조정기(pass transistor)가 입력-출력 전압 차이를 열로 방출. 입력이 24V이고 출력이 5V이면 19V 차이를 전부 열로 소모 | https://www.tutorialspoint.com/article/difference-between-smps-and-linear-power-supply | 높음 |
| 발열 원인 — 일반 충전기 | 전력 변환 과정에서 스위칭 소자, 트랜스포머, 정류 회로 내부 저항에서 손실 발생. 손실 에너지는 열로 방산. 어떤 변환기도 100% 효율 불가 | https://imiapower.com/why-does-my-charger-get-hot/ | 높음 |

### 추가 참고 자료

- 출처: https://namu.wiki/w/%EA%B5%90%EB%A5%98(%EC%A0%84%EA%B8%B0)
  요약: 교류의 발전·송전 장점(변압 용이, 장거리 전송 손실 적음)과 직류 기기 구동 시 변환 필요성 설명.

- 출처: https://www.wevolver.com/article/linear-vs-switching-power-supply
  요약: LPS와 SMPS의 기술적 차이, 효율·크기·소음·비용·용도 등 다각적 비교.

- 출처: https://www.agoda.com/ko-kr/travel-guides/south-korea/electric-socket-types-voltage-and-plug-compatibility-in-south-korea/
  요약: 한국 콘센트 220V/60Hz 규격, 충전기·어댑터의 호환 전압 범위(100–240V) 설명.

### writer 전달 사항 (2차 조사 보강)

- 강조할 내용:
  - "콘센트에서 나오는 220V AC는 전자기기가 직접 쓸 수 없다. 스마트폰은 DC 5V, 노트북은 DC 19V가 필요하다"는 전압 격차가 핵심 도입부 메시지.
  - LPS는 입출력 전압 차이를 열로 태워 낮춘다는 직관적 설명으로 발열 이유를 제시.
  - 비유: 직류=한 방향 강물, 교류=앞뒤로 흔들리는 파도.
  - 교류가 장거리 전송에 유리하고(발전소→가정), 전자기기는 직류가 필요하므로 변환 장치(SMPS)가 필수임을 연결 고리로 활용.
- 주의 사항 (불확실한 정보):
  - [미확인] LPS 효율 하한: 출처에 따라 30~40% 또는 40~60%로 편차 있음. "일반적으로 30~60% 수준으로 조건에 따라 차이가 크다"는 보수적 표현 권장.
  - 기기 요구 전압은 제조사·모델별로 다르므로 "일반적인 예시"임을 명시할 것.

---

## [2차 조사] 챕터 2: SMPS의 작동 원리 — 스위칭이 만드는 변환 조사 결과 - 2026-10-24

### 이 조사의 목적
대학교 1~2학년생이 SMPS 내부 동작(스위칭, PWM, 부품 역할, 소형화 원리)을 수식 없이 이해할 수 있도록 정확한 수치와 직관적 비유 자료를 보강한다.

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| 스위칭 주파수 범위 | 소비자용 SMPS 일반 범위: 20kHz~1MHz (대부분 어댑터·충전기: 50~500kHz). 역사적 진화: 1980년대 20~40kHz → 2020년대 1~2MHz | https://www.lcsc.com/blog/switched-mode-power-supply/ , https://industrialmonitordirect.com/blogs/knowledgebase/switch-mode-power-supply-history-mosfets-wall-warts-emi | 높음 |
| PWM 개념 | ON/OFF 비율(듀티 사이클)로 평균 전압 조절. ON 비율 크면 평균 전압 상승, 작으면 하강. 선풍기 속도를 빠른 ON/OFF 반복으로 조절하는 것과 동일 원리 | https://blog.daum.net/trts1004/12109425 , https://www.ariat-tech.com/blog/What-Is-Pulse-Width-Modulation(PWM)-Basic-Ideas-and-Uses.html | 높음 |
| 트랜스포머 역할 | 코일 감은 수 비율로 전압 변환(1차·2차 권선 원리). SMPS에서는 1차측과 2차측을 전기적으로 격리(절연)하여 감전 방지. 높은 주파수에서 동작하므로 소형화 가능 | https://ko.wikipedia.org/wiki/%EB%B3%80%EC%95%95%EA%B8%B0 , https://namu.wiki/w/SMPS | 높음 |
| 다이오드 역할 | 전류를 한 방향으로만 통과시키는 일방통행 밸브. 교류를 직류로 바꾸는 정류 회로에 핵심적으로 사용 | https://wiki.vctec.co.kr/imbedideu-ilban/breadboarding | 높음 |
| 캐패시터 역할 | 전기를 일시 저장했다가 방출하는 완충 장치. 아파트 물탱크처럼 전압 변동(맥류, 리플)을 평탄화하여 안정된 DC 출력 생성 | https://wiki.vctec.co.kr/imbedideu-ilban/breadboarding , https://namu.wiki/w/%EC%BB%A4%ED%8C%A8%EC%8B%9C%ED%84%B0 | 높음 |
| 스위칭 주파수 ↑ → 트랜스포머 소형화 | 주파수 높을수록 동일한 자속 얻기 위한 코어 크기와 권선 수 감소. 상용 60Hz 변압기 대비 50kHz 이상 동작 SMPS 트랜스포머는 수십 배 작아짐 | https://namu.wiki/w/SMPS , https://electronicmanufacturingservice.org/smps-circuit-design-which-switching-frequency-use/ | 높음 |

### 추가 참고 자료

- 출처: https://www.lcsc.com/blog/switched-mode-power-supply/
  요약: SMPS 설계 가이드. 스위칭 주파수·토폴로지·부품 선택 등 기술 전반. 수치 참고에 유용.

- 출처: https://en.wikipedia.org/wiki/Switched-mode_power_supply
  요약: SMPS 영문 위키백과. 구성요소, 원리, 분류, EMI 등 전반적 내용.

- 출처: https://www.sciencedirect.com/topics/engineering/switched-mode-power-supplies
  요약: SMPS 학술 개요. 스위칭 주파수 범위와 효율·손실의 절충 관계(trade-off) 설명.

### writer 전달 사항 (2차 조사 보강)

- 강조할 내용:
  - PWM 비유: "선풍기 ON/OFF를 초당 수만 번 반복하면 중간 속도처럼 느껴진다. SMPS는 이 원리로 출력 전압을 조절한다."
  - 트랜스포머 비유: "코일 감은 수를 조절하는 것은 기어 변속처럼 전압(힘)을 바꾸는 것."
  - 다이오드 비유: "물이 한쪽으로만 흐르는 일방통행 수문."
  - 캐패시터 비유: "전기 저수지 — 전압이 높을 때 충전, 낮을 때 방전하여 전압을 평탄하게."
  - 스위칭 주파수가 높아질수록 트랜스포머가 작아지는 원리 → SMPS가 스마트폰 충전기처럼 소형화될 수 있는 근본 이유.
- 주의 사항 (불확실한 정보):
  - 스위칭 주파수 범위는 제품 유형과 설계에 따라 매우 다양하므로 "일반적으로" 또는 "소비자용 제품 기준"이라는 단서를 붙일 것.
  - 스위칭 주파수 상승에 따른 소형화는 스위칭 손실 증가라는 trade-off가 있으나, 입문 수준 본문에서는 단순화하여 주석 또는 부연으로 처리 가능.

---

## [2차 조사] 챕터 3: SMPS의 응용과 안전 — 생활 속 전원공급장치 조사 결과 - 2026-10-24

### 이 조사의 목적
독자가 SMPS를 일상에서 어디서 만나는지 파악하고, 안전·인증 기준의 존재 이유를 이해할 수 있도록 응용 사례 및 규격 자료를 보강한다.

### 핵심 자료

| 항목 | 내용 요약 | 출처 | 신뢰도 |
|---|---|---|---|
| SMPS 응용 제품 목록 | 스마트폰 충전기, 노트북 어댑터, PC 파워서플라이, LED 조명 전원, 인터넷 공유기·셋톱박스, 전기자동차 충전기, 의료기기 전원 (7가지) | https://nalayang.com/smps-ed-part7/ , https://cnnvvv.com/news/what-is-smps-mostly-used-for/ | 높음 |
| EMI 발생 원인 | SMPS의 고속 스위칭(수십~수백 kHz)이 고조파 전자기파를 생성하여 주변 장치 간섭. SMPS 작동 시 라디오·TV 잡음 발생이 대표 사례 | https://www.panoxdisplay.com/ko/solution/what-is-electromagnetic-interference-emi/ , https://blog.doillabs.com/entry/EMI전자파-간섭란-무엇인가요-PCB-설계에서의-대응-방법-총정리 | 높음 |
| 전도성 EMI | 전원 배선·회로 경로를 통해 전파되는 전자기 간섭. 여러 기기가 동일 전원 공유 시 발생 빈도 높음 | https://elementkorea.kr/전자파-장해-시험-emi에-대한-완벽-가이드/ | 높음 |
| 방사성 EMI | 공기 중으로 방사되어 다른 장치에 영향. 거리와 차폐 상태에 따라 정도 차이 있음 | https://elementkorea.kr/전자파-장해-시험-emi에-대한-완벽-가이드/ | 높음 |
| KC 인증 (한국) | 한국 국가기술표준원 주관. 한국 시장 판매 필수. 시험 기관의 실험실 검증 방식 | https://elementkorea.kr/전자기기-인증-기준-한국-kc-vs-국제-ce-fcc-비교/ , https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/ | 높음 |
| CE 마크 (유럽) | EU 시장 진입 필수. 제조사 자기 선언 방식(Self-declaration). 인증 비용·기간이 비교적 낮음 | https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/ | 높음 |
| UL 인증 (미국) | 제3자 기관(UL)이 실제 검증. 법적 의무는 아니나 시장 사실상 필수. 세 인증 중 안전 기준이 가장 엄격한 편 | https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/ , https://tonful.com/ko/ce-vs-ul-certification-electrical-terminals/ | 높음 |

### 추가 참고 자료

- 출처: https://www.nemko.com/ko/blog/emc-vs-emi-whats-the-difference
  요약: EMI(전자파 간섭)와 EMC(전자기 적합성)의 차이. EMC는 EMI를 발생시키지도 않고 영향도 받지 않는 능력을 뜻함.

- 출처: https://k-rnd.com/electronics-certification-guide/
  요약: 전자제품 KC·CE·FCC·RoHS 인증 총정리. KC 인증 세부 분류(안전·EMC·전자파흡수율 등) 포함.

- 출처: https://www.kcrlab.co.kr/%ED%95%B4%EC%99%B8%EC%9D%B8%EC%A6%9D%EC%9D%84-%EB%B0%9B%EC%9D%80-%EC%A0%9C%ED%92%88%EC%9D%B8%EB%8D%B0-kc%EC%9D%B8%EC%A6%9D%EC%9D%84-%EB%98%90-%EB%B0%9B%EC%95%84%EC%95%BC-%ED%95%98%EB%82%98%EC%9A%94/
  요약: 해외 인증(CE, UL 등)을 취득해도 한국 판매 시 KC 인증 별도 필요 확인.

### writer 전달 사항 (2차 조사 보강)

- 강조할 내용:
  - 응용 목록 중 독자에게 친숙한 제품(스마트폰 충전기, 노트북 어댑터, 공유기)을 먼저 언급하여 친근감 형성.
  - EMI 설명 비유: "SMPS가 초당 수만 번 스위칭할 때 생기는 전자기 잡음은 형광등 켤 때 라디오에 잡음이 끼는 것과 같다."
  - KC·CE·UL 인증의 핵심 메시지: "이 마크가 붙은 제품은 각 나라의 안전 기준을 통과했다는 뜻."
- 주의 사항 (불확실한 정보):
  - CE 마크의 자기 선언 방식은 일부 제품군에서 제3자 검증이 병행되기도 하므로 "자기 선언 방식이 기본"이라는 표현이 정확함. 단정하지 말 것.
  - UL이 법적 의무가 아님에도 "사실상 필수"라는 표현은 업계 관행 기반이므로 단서 표현 권장.

---

## [2차 조사] 전체 수치 및 비유 정리 (writer 참조용) - 2026-10-24

### 수치 정리 (본문 사용 가능)

| 수치 | 값 | 비고 |
|---|---|---|
| 한국 콘센트 전압 | AC 220V, 60Hz | 한국전력 공식 규격 |
| 스마트폰 충전기 출력 | DC 5~9V | USB 표준 및 급속충전 기준 |
| 노트북 어댑터 출력 | DC 19~20V | 브랜드별 편차 있음 |
| LED 스트립 입력 | DC 12V 또는 24V | 제품 유형별 상이 |
| LPS 효율 [미확인-하한] | 30~60% | 출처별 편차, 보수적 표현 권장 |
| SMPS 효율 | 65~95% | 일반적 범위, 고효율 제품은 최대 95% |
| SMPS 스위칭 주파수(소비자용) | 50~500kHz (일반), 최대 2MHz (최신) | 제품 유형별 상이 |

### 비유 소재 목록 (2차 조사 확정)

| 개념 | 추천 비유 |
|---|---|
| 직류(DC) | 한쪽으로만 흐르는 강물 |
| 교류(AC) | 앞뒤로 반복되는 파도 |
| PWM 듀티 사이클 | 선풍기 ON/OFF를 빠르게 반복하여 중간 속도 구현 |
| 트랜스포머 | 기어 변속 (코일 감은 수로 전압 조절) |
| 다이오드 | 일방통행 수문 (전류를 한 방향으로만 통과) |
| 캐패시터 | 전기 저수지 (충·방전으로 전압 평탄화) |
| EMI | 형광등 켤 때 라디오에 끼는 잡음 |

### [미확인] 항목 목록 (2차 조사 기준)

1. LPS 효율 하한 수치: 출처에 따라 30~40% 또는 40~60%로 편차. "조건에 따라 30~60%" 범위 표현 권장.
2. 스위칭 주파수 상한: 기술 발전에 따라 2MHz 이상도 있으나 소비자 입문서 수준에서는 "수십~수백kHz" 표현이 안전.
