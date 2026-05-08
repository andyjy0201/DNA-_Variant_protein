요청하신 내용을 바탕으로 **DNA 변이 분석 및 단백질 영향 예측 리포트**를 가독성 높은 Markdown 형식으로 정돈해 드립니다. 깔끔한 구조와 이모지, 표를 활용하여 웹 대시보드 결과 화면처럼 구성했습니다.

---

# 🧬 DNA-Variant Protein Analyzer

> **DNA 서열 변이가 단백질의 구조적·기능적 변화에 미치는 영향을 분석하는 통합 파이프라인**

---

## 🚀 분석 파이프라인 개요

본 프로그램은 DNA 서열을 입력받아 단백질 수준의 변화를 4단계로 정밀 분석합니다.

1. **염기 서열 분석**: DNA → Amino Acid 서열 변환 및 최적 읽기 틀(ORF) 식별
2. **변이 지점 식별**: 야생형(WT)과 변이형(Mutant) 서열의 정렬 및 비교
3. **물리화학적 특성 분석**: `Biopython`을 이용한 5대 지표(분자량, pI, 불안정성 등) 계산
4. **기능적 영향 예측**: Meta AI의 `ESM-2` 언어 모델을 활용한 변이 치명도(Log-likelihood) 예측

---

## 📊 DNA 변이 분석 시각화 리포트

### 1️⃣ 서열 변환 및 변이 지점 식별

야생형과 변이형 사이의 DNA 서열 차이를 시각화하여 변이 지점을 식별합니다.

```text
WT DNA :  ATG GTG CAC CTG ACT CCT GAG GAG AAG TCT GCC GTT ACT GCC
           |   |   |   |   |   |  [!]  |   |   |   |   |   |   |
Mut DNA:  ATG GTG CAC CTG ACT CCT GTG GAG AAG TCT GCC GTT ACT GCC

```

> **분석 결과**: 7번째 코돈의 **GAG (Glu)** 가 **GTG (Val)** 로 치환된 **미스센스 돌연변이(Missense Mutation)** 가 확인되었습니다.

---

### 2️⃣ 단백질 물리화학적 특성 비교 (`Biopython`)

변이로 인해 변화된 단백질의 물리적 성질을 계산한 결과입니다.

| 분석 항목 | 야생형 (WT) | 변이형 (Mut) | 변화량 | 상태 |
| --- | --- | --- | --- | --- |
| **분자량 (Molecular Weight)** | 1,450.6 | 1,421.6 | -29.0 | 📉 감소 |
| **등전점 (pI)** | 4.37 | 5.12 | +0.75 | 📈 상승 |
| **불안정 지수 (Instability Index)** | 32.45 | 31.80 | -0.65 | 🟢 안정 |
| **지방족 지수 (Aliphatic Index)** | 85.20 | 92.50 | +7.30 | 📈 상승 |
| **친수성 지수 (GRAVY)** | -0.450 | -0.120 | +0.330 | 📉 소수성 증가 |

---

### 3️⃣ 기능적 영향 및 치명도 예측 (`ESM-2 Model`)

Meta AI의 단백질 언어 모델 ESM-2를 통해 예측된 변이의 치명적인 정도입니다.

#### 📍 ESM-2 Score Analysis

* **예측 점수 (Log-likelihood Difference):** `-8.42`
* **치명도 등급:** `High Risk (치명적)`

> **종합 의견**:
> 아미노산 서열에서 음전하를 띠는 **글루탐산(E)**이 비극성 소수성인 **발린(V)**으로 교체되었습니다. 이로 인해 단백질 표면의 전하 균형이 깨지고 친수성이 감소하여, 단백질의 3차 구조 접힘이나 용해도에 심각한 영향을 미칠 것으로 예측됩니다.

---

## 🛠️ 기술 스택 (Tech Stack)

* **Frontend**: Streamlit / React (Web Interface)
* **Bioinformatics**: `Biopython` (Sequence processing)
* **AI Model**: `ESM-2` (Evolutionary Scale Modeling by Meta AI)
* **Language**: Python 3.9+

---

보여드린 서열 변환 결과(Glu → Val)는 대표적인 유전병인 겸상 적혈구 빈혈증(Sickle Cell Anemia)의 변이 패턴과 유사합니다. 이와 같은 방식으로 다양한 유전 변이를 웹 환경에서 즉각적으로 분석할 수 있습니다.
