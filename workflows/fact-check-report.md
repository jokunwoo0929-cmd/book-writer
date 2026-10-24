# 사실 검증 보고서

## 이 검증의 목적
독자의 신뢰를 유지하기 위해(Why) 초고에 포함된 모든 수치·용어·사실 관계를 외부 출처와 교차 확인하여 오류를 표시한다(What).

---

## 챕터별 검증 결과

### 챕터 1: 전기를 '맞춤 제작'한다는 것
*(초고 v1 기준 — 이전 검증 사이클)*

| 항목 | 원문 내용 | 등급 | 비고 |
|---|---|---|---|
| 한국 콘센트 전압 | 220V, 60Hz의 교류 전기 | 확인됨 | 한국 표준 전압·주파수와 일치. KEPCO 및 다수 출처 교차 확인. |
| 스마트폰 필요 전압 | DC 5V | 조건부 확인됨 | 구형 USB-A 충전 표준(USB 2.0/3.0) 기준 5V는 정확하나, 현대 USB-C PD 충전기는 9V·15V·20V 등 다양한 전압을 지원함. 일반 독자 대상이므로 5V 기재 자체가 오류는 아니나, 보조 설명 추가 권고. |
| 노트북 필요 전압 | DC 19V | 수정 필요 | 19V는 ASUS, 레노버 아이디어패드 등 일부 제품에만 해당. 삼성 갤럭시북·LG 그램·레노버 씽크패드·Dell XPS·MacBook 등 다수 브랜드는 20V 사용. ASUS ROG·HP 계열은 19.5V 사용. 보다 정확한 기술은 "DC 19~20V" 범위 표기. |
| LPS 효율 범위 | 20~50% | 수정 필요 | 복수 기술 자료에서 선형 전원공급장치의 일반적 효율은 30~60% (표준형), 40~50% (대표값)로 확인됨. 하한 20%는 매우 극단적인 조건(입출력 전압 차이가 큰 경우)에 해당하며, 일반적 기술로는 과소 추정에 해당함. "30~60%" 또는 "40~50%"로 수정 권고. |
| SMPS 효율 범위 | 65~95% | 확인됨 | 다수 기술 문헌에서 SMPS 효율 80~95%, 일부 80~90%로 기재. 65% 하한은 구형·저효율 제품 포함 시 성립 가능. 허용 범위 내. |
| LPS 작동 원리 | 남는 전압을 열로 태워 버리는 방식 | 확인됨 | 선형 레귤레이터의 열 소산(heat dissipation) 원리와 일치. 기술적으로 정확. |

### 챕터 2: SMPS는 어떻게 작동하는가
*(초고 v1 기준 — 이전 검증 사이클)*

| 항목 | 원문 내용 | 등급 | 비고 |
|---|---|---|---|
| SMPS 스위칭 주파수 | 수십~수백 kHz의 초고속 | 확인됨 | 기술 문헌에서 소비자용 SMPS의 스위칭 주파수는 20kHz~500kHz(일반적으로 50~500kHz) 범위로 확인됨. "수십~수백 kHz"는 이 범위와 부합. |
| PWM 용어 풀이 | PWM(펄스폭변조) | 확인됨 | PWM은 Pulse Width Modulation의 약어이며, 한국어로 펄스폭변조가 정확한 번역. |
| 듀티 사이클 개념 | 켜져 있는 시간의 비율(듀티 사이클) | 확인됨 | 듀티 사이클(duty cycle)은 전체 주기 대비 ON 상태 시간의 비율로 정의되며, 원문 설명과 일치. |
| 트랜스포머 역할 | 높은 전압을 낮은 전압으로, 혹은 그 반대로 바꾸는 번역기 | 확인됨 | 변압기(transformer)의 변압 기능을 정확히 설명. 양방향 변환 가능 묘사도 정확. |
| 트랜스포머 소형화 이유 | 주파수를 높여 놓았기 때문에 LPS의 트랜스포머보다 훨씬 작아도 충분히 작동 | 확인됨 | 자기 부품의 크기는 주파수에 반비례함. 고주파로 동작하는 SMPS의 트랜스포머가 소형화 가능한 것은 전력전자 기본 원리와 일치. |
| 다이오드 역할 | 전기가 한쪽 방향으로만 흐르게 하는 일방통행 도로, 교류를 직류로 바꿔 주는 정류 역할 | 확인됨 | 다이오드의 단방향 도전 특성 및 정류(rectification) 기능에 대한 설명이 정확. |
| 캐패시터 역할 | 전기를 잠깐 모아 두는 저수지, 미세한 전압 변동을 흡수 | 확인됨 | 캐패시터(커패시터)의 전하 저장 기능과 전압 리플(ripple) 평활화(smoothing) 역할에 대한 설명이 정확. |

### 챕터 3: SMPS가 만드는 세상
*(초고 v1 기준 — 이전 검증 사이클)*

| 항목 | 원문 내용 | 등급 | 비고 |
|---|---|---|---|
| SMPS 응용 사례 목록 | 스마트폰 충전기, 노트북 어댑터, LED 조명 드라이버, PC ATX 파워 서플라이, 산업용 제어 장치 | 확인됨 | 열거된 모든 사례는 실제로 SMPS를 채용하는 기기들로 기술 문헌과 일치. |
| 전자파 간섭 개념 | 초고속 스위칭이 전자파를 발생시킨다, 이를 EMI(전자파 간섭)라 한다 | 확인됨 | SMPS의 고속 스위칭이 전도성 및 방사성 EMI를 발생시킨다는 것은 전력전자 분야에서 잘 알려진 사실. |
| 전자레인지-라디오 비유 | 전자레인지를 켰을 때 근처 라디오에 잡음이 생기는 것과 같은 원리 | 미확인 | 전자레인지의 마그네트론이 발생시키는 2.4GHz 대역 전자파와 SMPS의 스위칭 노이즈(주로 20kHz~수백kHz 대역)는 주파수 대역이 상이함. 비유 자체는 독자 이해를 돕는 용도이나 기술적으로 엄밀하지 않음. "형광등을 켤 때 라디오에 잡음이 생기는 것"이 더 정확한 유사 사례. |
| KC 인증 국가 | KC(한국) | 확인됨 | KC(Korea Certification)는 한국기술표준원(KATS) 주관의 한국 안전 인증 마크. |
| CE 인증 국가 | CE(유럽) | 확인됨 | CE(Conformité Européenne)는 EU 판매 제품 필수 인증 마크. |
| UL 인증 국가 | UL(미국) | 확인됨 | UL(Underwriters Laboratories)은 미국 안전 인증 기관 및 마크. |

---

## 검증 결과 요약 (초고 v1)

| 등급 | 건수 | 해당 항목 |
|---|---|---|
| 확인됨 | 13건 | 한국 콘센트 전압/주파수, SMPS 효율, LPS 원리, 스위칭 주파수, PWM, 듀티 사이클, 트랜스포머·다이오드·캐패시터 역할, SMPS 응용 사례, EMI 개념, KC/CE/UL 인증 |
| 수정 필요 | 2건 | 노트북 DC 전압(19V 단일 표기), LPS 효율 하한(20%) |
| 조건부 확인됨 | 1건 | 스마트폰 DC 5V (USB-A 기준 정확, USB-C PD 시대에는 보완 설명 권고) |
| 미확인 | 1건 | 전자레인지-라디오 비유의 기술적 정확성 |

---

## reviewer 전달 사항 (초고 v1)

- 오류 건수: 2건 (수정 필요)
- 불확실 항목: 1건 (미확인), 1건 (조건부 확인)
- 우선 수정 권고 항목:

  1. **[수정 필요] 1장 1.1 — 노트북 DC 전압**
     - 원문: "노트북은 DC 19V가 필요하다"
     - 수정 제안: "노트북은 DC 19~20V가 필요하다"
     - 근거: 삼성, LG, 레노버 씽크패드, Dell, Apple 등 주요 브랜드는 20V를 사용하며, ASUS 등 일부 브랜드만 19V 또는 19.5V를 사용함.
     - 출처: [노트북 어댑터 정격 확인과 호환 충전기 고르는 법](https://digi-royal.com/laptop-adapter/)

  2. **[수정 필요] 1장 1.1 — LPS 효율 하한**
     - 원문: "효율이 20~50%에 불과하다"
     - 수정 제안: "효율이 30~60%에 불과하다" 또는 "효율이 40~50% 수준에 불과하다"
     - 근거: 복수의 기술 문헌에서 표준형 선형 전원공급장치의 효율은 40~50% (대표값) 또는 30~60% 범위로 확인됨. 하한 20%는 극단적인 전압 강하 조건에서만 성립하는 수치이며, 일반적 서술로는 부적절함.
     - 출처: [What are the Efficiency Levels of different Power Supplies?](https://www.circuitbread.com/ee-faq/what-are-the-efficiency-levels-of-different-power-supplies), [Linear Regulated vs. Switch Mode Power Supply](https://www.autodesk.com/products/fusion-360/blog/linear-regulated-vs-switch-mode-power-supply/)

  3. **[미확인] 3장 3.2 — 전자레인지-라디오 비유**
     - 원문: "전자레인지를 켰을 때 근처 라디오에 잡음이 생기는 것과 같은 원리"
     - 검토 의견: 전자레인지(2.4GHz 마그네트론)와 SMPS 스위칭 노이즈(20kHz~수백kHz)는 주파수 대역이 크게 다름. 비유가 독자의 오해를 유발할 수 있음. 더 정확한 비유로 대체하거나, 비유임을 명시하는 문구 추가 권고.
     - 대안 비유 제안: "형광등이나 모터를 켤 때 라디오에 잡음이 생기는 것과 유사한 원리"

  4. **[조건부 확인] 1장 1.1 — 스마트폰 DC 5V**
     - 원문: "스마트폰은 DC 5V"
     - 검토 의견: USB-A 충전(USB 2.0/3.0) 기준 5V는 정확하나, 현대 스마트폰의 대부분은 USB-C PD를 통해 9V·15V·20V로 급속 충전함. 일반 독자 대상이므로 현시점의 독자에게 혼란을 줄 수 있음. "(일반 USB 충전 기준 5V)" 등의 주석 추가 권고.

---

*검증 기준일: 2026-10-24 (초고 v1)*
*검증 방법: researcher 조사 노트 대조 + 웹 교차 검색 (한국 KEPCO, 기술 문헌, 제조사 사양 자료)*

---

---

## Fact-Check 보고서 — 2026-10-24 (현행 초고 v2 기준)

> 이 섹션은 editor가 v1 검증 결과를 반영하여 수정한 현행 `output/BOOK.md`(v2)에 대해 챕터 1을 재검증한 결과다.

### 이 검증의 목적
독자의 신뢰를 유지하기 위해(Why) 현행 초고 챕터 1의 수치·사실 관계가 외부 출처와 일치하는지 교차 확인한다(What).

---

### 챕터 1: 전원공급장치란 무엇인가 — 왜 변환이 필요한가 (현행 v2)

#### 1.1 우리 주변의 전기: 교류(AC)와 직류(DC)의 차이

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 1 | 1.1 | 한국 가정용 콘센트 220V, 60Hz 규격 | 정확 | 없음 | 한국전력(KEPCO) 공식 규격, [한국의 콘센트 종류·전압·플러그 호환성 (Agoda)](https://www.agoda.com/ko-kr/travel-guides/south-korea/electric-socket-types-voltage-and-plug-compatibility-in-south-korea/), [세계의 전압·콘센트 (Tenso)](https://www.tenso.com/kr/static/guide_advice_voltage) |
| 1 | 1.1 | 스마트폰 충전기 출력 전압 DC 5~9V | 정확 | 없음. 단, 5V는 기본 USB 표준, 9V 이상은 USB PD 고속 충전 규격에 해당. 범위 표기("5~9V")는 현재 보편적인 충전기 스펙을 포괄함. | [USB PD 나무위키](https://namu.wiki/w/USB%20PD), [Smartphone Charger Voltage Explained (asmr.education)](https://asmr.education/faq/chargers/smartphone-charger-voltage-standard-fast-charging) |
| 1 | 1.1 | 노트북 어댑터 출력 전압 DC 19~20V | 정확 | 없음. v1의 "DC 19V" 단일 표기 오류가 "DC 19~20V"로 이미 수정됨. ASUS 계열 19V, 다수 브랜드 20V, HP 일부 19.5V 등을 "19~20V" 범위로 포괄하는 것은 적절. | [ASUS 노트북 어댑터 사양 (ASUS 공식)](https://www.asus.com/kr/support/faq/1015066/), [노트북 어댑터 정격 확인 가이드 (digi-royal)](https://digi-royal.com/laptop-adapter/) |

#### 1.2 선형 전원공급장치(LPS)의 한계와 SMPS의 등장

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 1 | 1.2 | LPS 효율 30~60%, 나머지는 열로 소산. "조건에 따라 차이가 크다" 단서 병기 | 정확 | 없음. v1의 "20~50%" 오류가 "30~60%"로 이미 수정됨. 다수 기술 문헌에서 표준형 LPS 효율은 30~50% 또는 40~50%로 확인되며, LDO 변형 포함 시 최대 60~70%까지 가능. "30~60%" 범위 표기 및 단서 병기는 기술적으로 적절. | [What are the Efficiency Levels of different Power Supplies? (CircuitBread)](https://www.circuitbread.com/ee-faq/what-are-the-efficiency-levels-of-different-power-supplies), [Linear Regulated vs. Switch Mode Power Supply (Autodesk/Fusion 360)](https://www.autodesk.com/products/fusion-360/blog/linear-regulated-vs-switch-mode-power-supply/) |
| 1 | 1.2 | SMPS 효율 65~95% | 정확 | 없음. 다수 기술 문헌에서 SMPS 효율은 일반적으로 70~95%, 최신 LLC 공진 방식은 95% 이상 달성 가능. "65~95%" 하한 65%는 구형·저효율 제품을 포함한 범위로 수용 가능. | [Understanding Switched-Mode Power Supplies (Avnet Abacus)](https://my.avnet.com/abacus/solutions/technologies/power/the-design-engineers-guide/switched-mode-power-supplies/), [Switch Mode Power Supply Complete Guide (usb-guide.com)](https://usb-guide.com/switch-mode-power-supply-smps-complete-guide-how-it-works-types-topologies-key-facts/) |
| 1 | 1.2 | LED 스트립 입력 전압 DC 12V 또는 24V | 정확 | 없음. LED 스트립의 주요 공급 전압은 시장 표준으로 12V DC 및 24V DC가 확립되어 있음. | [12V vs 24V LED Strip Lights (inspiredled)](https://www.inspiredled.com/led-buying-guides/12v-vs-24v-led-strip-lights-which-should-you-choose/), [LED Strip Voltage Guide (waveformlighting)](https://www.waveformlighting.com/home-residential/how-to-choose-a-power-supply-for-your-led-strip-project) |
| 1 | 1.2 | 24V 입력에서 5V 출력 시 19V 전압 강하가 전부 열로 낭비 | 정확 | 없음. 선형 레귤레이터의 열 소산 원리 — 입출력 전압차 × 전류 = 손실 전력(열). 기술적으로 정확한 설명. | [Linear vs Switching Power Supply Guide (omch.com)](https://www.omch.com/linear-vs-switching-power-supply/) |

---

### 챕터 1 검증 결과 요약

| 등급 | 건수 | 해당 항목 |
|---|---|---|
| 정확 | 6건 | 한국 콘센트 220V/60Hz, 스마트폰 DC 5~9V, 노트북 DC 19~20V, LPS 효율 30~60%, SMPS 효율 65~95%, LED 스트립 12V/24V |
| 오류 | 0건 | — |
| 불확실 | 0건 | — |

### reviewer 전달 사항 (챕터 1)
- 오류 건수: 0건
- 불확실 항목: 0건
- 우선 수정 권고 항목: 없음
- 특기 사항: v1에서 지적된 수정 필요 2건(노트북 전압, LPS 효율)이 현행 v2에서 모두 올바르게 반영되어 있음. 챕터 1의 모든 수치는 외부 출처와 일치한다.

---

*검증 기준일: 2026-10-24 (현행 초고 v2)*
*검증 방법: 웹 교차 검색 (한국전력 규격, ASUS 공식, 기술 문헌 다수)*

---

## 챕터 2: SMPS의 작동 원리 — 스위칭이 만드는 변환 (현행 v2)

> 이 섹션은 현행 `output/BOOK.md`(v2)의 챕터 2를 검증한 결과다.

### 이 검증의 목적
독자의 신뢰를 유지하기 위해(Why) 챕터 2에 기술된 스위칭 주파수 수치·PWM 원리·핵심 부품 역할의 정확성을 외부 출처와 교차 확인한다(What).

---

#### 2.1 스위칭의 개념과 PWM(펄스폭변조)

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 2 | 2.1 | 소비자용 SMPS 스위칭 주파수 일반 범위 50~500kHz | 조건부 정확 | 없음. 단, 주류 소비자용 제품의 실제 스위칭 주파수 중심대는 100~500kHz이며, 50kHz 하한은 구형·저비용 제품에 해당함. 현행 본문에 "소비자용 제품 기준으로 일반적으로" 및 "제품 유형과 설계에 따라 범위가 크게 다를 수 있다"는 단서가 병기되어 있어 기술적으로 허용 범위 내임. | [SMPS Complete Design Guide (LCSC Blog)](https://www.lcsc.com/blog/switched-mode-power-supply/), [Transformer Core Area vs Power Rating (industrialmonitordirect.com)](https://industrialmonitordirect.com/blogs/knowledgebase/transformer-core-area-vs-power-rating-explained), [EMF Testing & EMI Diagnostics (elexana.com)](https://www.elexana.com/switch-mode-power-supplies-frequencies-emc-compliance-and-mitigation-techniques) |
| 2 | 2.1 | 최신 SMPS 스위칭 주파수 최대 1~2MHz | 정확 | 없음. GaN(질화갈륨) 및 SiC(탄화규소) 기반 최신 설계에서 1~3MHz 동작이 확인됨. USB-C PD 고속 충전기 및 EV 충전 컨버터에서 1~2MHz 실측치 다수 보고됨. | [How to Use GaN Technology in Switch-Mode Power (Analog Devices)](https://www.analog.com/media/en/technical-documentation/technical-articles/a1165850-how-to-use-gallium-nitride-technology-in-switch-mode-power.pdf), [GaN-Based DC-DC converters for EV fast charging (ScienceDirect)](https://www.sciencedirect.com/science/article/pii/S2590123025036023) |
| 2 | 2.1 | PWM 듀티 사이클 원리 — ON 시간 비율이 클수록 평균 전압 상승 | 정확 | 없음. PWM 듀티 사이클과 평균 전압의 선형 비례 관계(V_avg = V_peak × D/100)는 전력전자 기본 원리로서 다수 문헌에서 확인됨. "ON 시간이 전체의 80%라면 출력 전압은 높고, 20%라면 낮아진다"는 서술도 이 원리에 부합함. | [What Is a PWM Signal? (Wevolver)](https://www.wevolver.com/article/what-is-a-pwm-signal-fundamentals-and-practical-applications-for-engineers), [PWM (ecrionix.org)](https://ecrionix.org/digital-electronics/pwm/) |

#### 2.2 핵심 부품의 역할: 트랜스포머, 다이오드, 캐패시터

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 2 | 2.2 | 60Hz 상용 변압기 대비 50kHz 이상 SMPS 트랜스포머가 수십 배 소형화 가능 | 조건부 정확 | 없음. 단, "수십 배" 표현에 대한 추가 설명: 주파수-부피 관계 분석에 따르면 100kHz 트랜스포머는 60Hz 대비 약 1/1,650 수준의 코어 면적이 가능하며, 1MHz에서는 동일 전력 처리 시 부피가 약 2.5%에 불과하다는 데이터가 있음. "수십 배"는 오히려 보수적인 표현으로 볼 수 있으나, 현행 본문에 "설계 조건에 따라 다를 수 있으므로" 단서가 병기되어 있어 허용 범위 내임. | [Transformer Core Area vs Power Rating (industrialmonitordirect.com)](https://industrialmonitordirect.com/blogs/knowledgebase/transformer-core-area-vs-power-rating-explained), [Switchmode Power Supply Primer (sound-au.com)](https://sound-au.com/articles/smps-primer.html), [SMPS Transformer Guide (electronics.alibaba.com)](https://electronics.alibaba.com/buyingguides/smps-transformer-guide-how-to-choose-use-right) |
| 2 | 2.2 | 다이오드가 정류(교류→직류 변환) 역할을 수행 | 정확 | 없음. 다이오드의 단방향 도전 특성에 의한 정류 기능은 전력전자 기본 원리임. SMPS에서는 입력단과 출력단 양쪽에서 정류 역할을 수행한다는 점도 기술 문헌과 일치함. | [Rectifier Diodes Explained (mccsemi.com)](https://solutions.mccsemi.com/rectifier-diodes-explained-a-complete-engineers-guide-to-types-and-applications), [AC to DC Converter Basics (LCSC Blog)](https://www.lcsc.com/blog/ac-to-dc-converter-basics/), [Bridge Rectifier and Diode Selection Guide (kingtronics.com)](https://www.kingtronics.com/news/Product/bridge-rectifier-and-diode-selection-guide-smps-power-design) |
| 2 | 2.2 | 캐패시터가 출력 전압 평활(Smoothing) 역할 수행 | 정확 | 없음. 캐패시터가 정류 후 전압 리플(ripple)을 평탄화(smoothing)하는 역할은 전력전자 기본 원리로서 다수 문헌에서 확인됨. "전압이 높을 때 전하를 저장했다가 낮아질 때 방출"하는 동작 설명도 기술적으로 정확함. | [Capacitor-input filter (Wikipedia)](https://en.wikipedia.org/wiki/Capacitor-input_filter), [Smoothing - DC Power Supply design (skillbank.co.uk)](https://www.skillbank.co.uk/psu/smoothing.htm), [Power Supply Capacitor (PCBSync)](https://pcbsync.com/power-supply-capacitor/) |

---

### 챕터 2 검증 결과 요약

| 등급 | 건수 | 해당 항목 |
|---|---|---|
| 정확 | 4건 | 최신 스위칭 주파수 1~2MHz, PWM 듀티 사이클 원리, 다이오드 정류 역할, 캐패시터 평활 역할 |
| 조건부 정확 | 2건 | 소비자용 스위칭 주파수 50~500kHz (단서 병기로 허용), 트랜스포머 소형화 "수십 배" (단서 병기로 허용) |
| 오류 | 0건 | — |
| 불확실 | 0건 | — |

### 챕터 2 reviewer 전달 사항
- 오류 건수: 0건
- 불확실 항목: 0건
- 우선 수정 권고 항목: 없음
- 특기 사항:
  - 스위칭 주파수 하한 "50kHz"는 구형·저비용 제품 기준이며, 현재 주류 소비자 제품(ATX 파워, 저가 충전기 포함)의 일반 범위는 100~500kHz에 해당함. 본문에 단서 문구가 이미 병기되어 있어 별도 수정은 불필요하지만, reviewer가 독자 이해 측면에서 "100~500kHz" 표기로 정밀화를 권고하는 것도 고려할 수 있음.
  - 트랜스포머 소형화 수치 "수십 배"는 기술적으로 보수적인 표현임. 실제로는 주파수-부피 관계상 수백~수천 배까지도 가능하나, 설계 조건 편차가 크므로 현행 "수십 배" 표기와 단서 병기 조합은 독자 오해를 방지하는 데 적절함.
  - 챕터 2의 모든 기술 내용(PWM 원리, 다이오드 정류, 캐패시터 평활)은 전력전자 기본 원리와 완전히 일치하며, 일반 독자 대상 설명 수준으로 기술적 정확성이 충분히 확보되어 있음.

---

*검증 기준일: 2026-10-24 (현행 초고 v2)*
*검증 방법: 웹 교차 검색 (LCSC Blog, Analog Devices, Wevolver, industrialmonitordirect.com, ScienceDirect, kingtronics.com 등 기술 문헌 다수)*

---

## 챕터 3: SMPS의 응용과 안전 — 생활 속 전원공급장치 (현행 v2)

> 이 섹션은 현행 `output/BOOK.md`(v2)의 챕터 3을 검증한 결과다.

### 이 검증의 목적
독자의 신뢰를 유지하기 위해(Why) 챕터 3에 기술된 SMPS 실생활 적용 사례·EMI 경로 구분·KC·CE·UL 안전 인증 기준의 정확성을 외부 출처와 교차 확인한다(What).

---

#### 3.1 실생활 속 SMPS 적용 사례

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 3 | 3.1 | 스마트폰 충전기·노트북 어댑터·PC 파워서플라이·LED 조명 전원·인터넷 공유기·셋톱박스가 SMPS 방식으로 동작한다 | 정확 | 없음. 열거된 모든 기기는 실제 SMPS(스위칭 방식) 전원 회로를 채용하며, 이는 나무위키·디바이스마트·LED 조명 전원 판매 자료 등 다수 출처에서 확인됨. 특히 공유기·셋톱박스 전원 어댑터도 SMPS 방식 DC 어댑터가 표준임. | [SMPS - 나무위키](https://namu.wiki/w/SMPS), [LED 조명 안정기 컨버터 SMPS (eoie.kr)](https://eoie.kr/product/led-%EC%A1%B0%EB%AA%85-%EC%95%88%EC%A0%95%EA%B8%B0-%EC%BB%A8%EB%B2%84%ED%84%B0-%ED%8C%8C%EC%9B%8C%EC%84%9C%ED%94%8C%EB%9D%BC%EC%9D%B4-smps-%EB%B0%A9%EC%88%98-%EC%8A%AC%EB%A6%BC-100w-12v/1141/), [전원아답터/SMPS (디바이스마트)](https://www.devicemart.co.kr/goods/catalog?code=000700040003) |

#### 3.2 전자파 간섭(EMI)과 안전 인증 기준

| 챕터 | 위치 | 원문 내용 | 검증 결과 | 수정 제안 | 출처 |
|---|---|---|---|---|---|
| 3 | 3.2 | EMI 전도성 경로(전원 배선을 타고 전도) 및 방사성 경로(공기 중으로 방사) 구분 | 정확 | 없음. 전도성 EMI(Conducted EMI)는 물리적 전기 경로(전원선·배선)를 통해 전파되고, 방사성 EMI(Radiated EMI)는 공간(공기 중)을 통해 전파되는 구분은 전자기 이론의 기본 원리로서 다수 출처에서 확인됨. | [Electromagnetic Interference - Coupling Mechanisms (GeeksforGeeks)](https://www.geeksforgeeks.org/electronics-engineering/electromagnetic-interference/), [Common EMI Sources and Propagation Paths (allpcb.com)](https://www.allpcb.com/allelectrohub/common-emi-sources-and-propagation-paths), [What is EMI? (electrical4u.com)](https://www.electrical4u.com/electromagnetic-interference/) |
| 3 | 3.2 | 형광등을 켤 때 라디오에 잡음이 끼는 것처럼 — EMI 비유 | 정확 | 없음. 현행 v2에서는 이전 v1의 '전자레인지-라디오 비유'가 '형광등을 켤 때 라디오에 잡음이 끼는 것처럼'으로 이미 교체됨. 형광등(전자식 안정기 포함)은 고주파 스위칭 노이즈를 발생시키며, SMPS의 EMI와 주파수 대역이 유사하여 적절한 비유임. | [FCC — 라디오·TV 및 전화 신호 간섭](https://www.fcc.gov/consumers/guides/radio-tv-mic-jeonhwa-sinho-ganseob), [EMI란 무엇인가요? (blog.yjpcb.kr)](https://blog.yjpcb.kr/entry/EMI%EC%A0%84%EC%9E%90%ED%8C%8C-%EA%B0%84%EC%84%AD%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94-PCB-%EC%84%A4%EA%B3%84%EC%97%90%EC%84%9C%EC%9D%98-%EB%8C%80%EC%9D%91-%EB%B0%A9%EB%B2%95-%EC%B4%9D%EC%A0%95%EB%A6%AC) |
| 3 | 3.2 | KC 마크: 한국 시장 판매 필수, 공인 시험 기관 검증 방식 | 정확 | 없음. KC(Korea Certification)는 전기용품 및 생활용품 안전관리법에 근거한 한국 강제 인증 제도이며, KTL·KTR·KTC 등 국가 지정 공인 시험 기관에서 검증을 받아야 함. 한국 시장 판매 시 법적 필수 인증임. | [KC 인증 완벽 가이드 (elementkorea.kr)](https://elementkorea.kr/kc-%EC%9D%B8%EC%A6%9D-%EC%99%84%EB%B2%BD-%EA%B0%80%EC%9D%B4%EB%93%9C-%EC%9D%B8%EC%A6%9D-%EC%A1%B0%ED%9A%8C%EB%B6%80%ED%84%B0-%EC%A7%84%ED%96%89-%EC%A0%88%EC%B0%A8-%EB%B0%8F-%EB%B9%84%EC%9A%A9/), [KC 인증 (Nemko)](https://www.nemko.com/product-certification/kc-certification), [안전인증 (KCL)](https://www.kcl.re.kr/site/homepage/menu/viewMenu.do?menuid=001012007001) |
| 3 | 3.2 | CE 마크: EU 시장 진입 필수, 제조사 자기 선언 방식 | 조건부 정확 | 수정 제안: "[검증 필요]" 태그 해제 가능. 단, "제조사가 유럽 기준을 충족한다고 선언한 표시"는 기본 방식(DoC)으로 정확하나, 본문에 이미 "[검증 필요: 제품 유형에 따라 제3자 검증이 추가될 수 있으며 세부 절차는 제품군마다 다르다]" 단서가 태그 형태로 삽입되어 있음. 해당 단서 내용은 사실이므로 태그를 해제하고 본문에 편입하거나 간략 주석으로 전환 권고. | [CE 인증 가이드 (elementkorea.kr)](https://elementkorea.kr/ce-%EC%9D%B8%EC%A6%9D-%EA%B0%80%EC%9D%B4%EB%93%9C-%EC%9C%A0%EB%9F%BD-%EC%8B%9C%EC%9E%A5-%EC%A7%84%EC%B6%9C%EC%9D%98-%ED%95%84%EC%88%98-%EC%97%B4%EC%87%A0/), [CE vs UL vs FCC Marks (ecocomply.ai)](https://ecocomply.ai/blog/ce-mark-vs-ul-vs-fcc-certifications), [KC vs CE vs UL 비교 (ufinebattery.com)](https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/) |
| 3 | 3.2 | UL 마크: 미국 시장에서 사실상 필수로 통용, 독립적인 제3자 기관 검증, 세 인증 중 가장 엄격한 기준 | 조건부 정확 | 없음. 세부 사항 확인: (1) "사실상 필수" — 연방법 차원의 법적 의무는 아니나, 지역 전기 코드(NEC)·소매 유통 요건(Amazon, Walmart 등)·보험 요건 등으로 인해 사실상 필수로 통용된다는 서술은 정확함. (2) "독립적인 제3자 기관 검증" — UL은 NRTL(국가 공인 시험 기관)로서 연방 정부 인정 제3자 검증 기관이므로 정확함. (3) "세 인증 중 가장 엄격" — 복수의 비교 자료에서 "UL이 KC·CE 중 가장 엄격한 시험 기준"으로 일치되게 확인됨. 현행 본문에 "법적 의무 여부는 제품 유형에 따라 다를 수 있다"는 단서가 이미 병기되어 있어 허용 범위 내임. | [Is UL Certification Required in the USA (legalclarity.org)](https://legalclarity.org/is-ul-certification-required-in-the-usa/), [KC vs CE vs UL 비교 (ufinebattery.com)](https://www.ufinebattery.com/ko/blog/kc-vs-ce-vs-ul-certification-comparison-guide/), [CE vs UL vs FCC Marks (ecocomply.ai)](https://ecocomply.ai/blog/ce-mark-vs-ul-vs-fcc-certifications), [UL Certification for Electrical Enclosures (eabel.net)](https://www.eabel.net/knowledge-of-electrical-enclosures-en/ul-certification-explained-why-electrical-products-need-ul-approval-to-enter-the-u-s-market/) |

---

### 챕터 3 검증 결과 요약

| 등급 | 건수 | 해당 항목 |
|---|---|---|
| 정확 | 3건 | SMPS 실생활 적용 사례(스마트폰 충전기 등 6종), EMI 전도성·방사성 경로 구분, 형광등-라디오 EMI 비유(v2 수정 반영) |
| 조건부 정확 | 2건 | CE 마크 자기 선언 방식(기본 방식은 정확, 단서 태그 처리 방식 정리 권고), UL 마크 "사실상 필수·가장 엄격" (단서 병기로 허용) |
| 오류 | 0건 | — |
| 불확실 | 0건 | — |

### 챕터 3 reviewer 전달 사항
- 오류 건수: 0건
- 불확실 항목: 0건
- 우선 수정 권고 항목:
  1. **[태그 정리 권고] 3.2 — CE 마크 [검증 필요] 태그**
     - 현행 본문 중 "[검증 필요: CE 마크는 제품 유형에 따라 제3자 검증이 추가될 수 있으며 세부 절차는 제품군마다 다르다]"라는 태그가 그대로 잔존해 있음.
     - 검증 결과: 해당 단서 내용은 사실이므로 "[검증 필요]" 태그를 제거하고 내용을 정식 문장 또는 괄호 주석으로 전환하도록 권고함.
     - 수정 제안 예시: "CE 마크는 기본적으로 제조사 자기 선언 방식이지만, 의료기기·기계류 등 위험도가 높은 제품군에서는 공인 기관(Notified Body)의 제3자 검증이 필수적으로 요구된다."
- 특기 사항:
  - KC 인증의 "공인 시험 기관 검증 필수" 서술은 KTL·KTR·KTC 등 국가 지정 기관 검증 요건과 일치하며 정확함.
  - UL의 "사실상 필수" 표현은 연방법상 선택 사항이나 지역 코드·소매 요건으로 인해 실질적 필수로 통용된다는 점에서 본문 표현이 적절함.
  - 챕터 3의 형광등 비유는 v1 검증에서 지적된 전자레인지 비유 문제가 올바르게 수정되어 있으며, 이제 기술적으로 적합한 비유임.

---

*검증 기준일: 2026-10-24 (현행 초고 v2)*
*검증 방법: 웹 교차 검색 (elementkorea.kr, ufinebattery.com, ecocomply.ai, legalclarity.org, GeeksforGeeks, allpcb.com 등 기술·인증 문헌 다수)*

---

## 3개 챕터 전체 검증 결과 최종 요약 (현행 v2)

| 챕터 | 정확 | 조건부 정확 | 오류 | 불확실 | 잔존 태그 |
|---|---|---|---|---|---|
| 챕터 1 | 6건 | 0건 | 0건 | 0건 | 없음 |
| 챕터 2 | 4건 | 2건 | 0건 | 0건 | 없음 |
| 챕터 3 | 3건 | 2건 | 0건 | 0건 | [검증 필요] 태그 1건 잔존 |
| **합계** | **13건** | **4건** | **0건** | **0건** | **1건** |

### 전체 reviewer 필수 처리 항목
1. **[태그 정리 필수] 챕터 3 3.2 — CE 마크 [검증 필요] 태그 잔존**: 내용은 사실이므로 태그를 제거하고 본문 문장으로 편입 또는 괄호 주석으로 전환할 것.
2. **[참고] 챕터 2 조건부 정확 2건**: 스위칭 주파수 50kHz 하한 및 트랜스포머 소형화 "수십 배"는 단서 병기로 허용 범위 내이나, reviewer가 독자 친화적 표현으로 추가 정밀화 여부를 검토할 수 있음.

*최종 검증 완료: 2026-10-24*
