
## **Marginal Structural Models (MSMs)

* MSM을 바라보기 앞서
* DiD  vs MSM

- **공통점**: 둘 다 관찰 데이터에서 특정 '치료(intervention)'의 인과적 효과를 추정하는 것을 목표
- **차이점**: 다루는 데이터의 형식과 해결하고자 하는 문제 상황에 차이가 존재
    - **DiD (Difference-in-Differences)**
        - 주로 정책 변화, 프로그램 도입과 같은 '치료'를 분석함.
        - 특히 Staggered DiD는 여러 집단이 치료를 받는 시점이 제각각일 때 유용하게 활용됨.
        - 데이터는 주로 여러 개체(집단)를 여러 시점에 걸쳐 관찰하는 패널 데이터
        - '치료'가 시작되는 시점이 비교적 명확하며, 치료 전후의 변화를 비교하는 데 강점이 있음.
    - **MSM (Marginal Structural Models)**
        - 개인 수준에서 '치료' 내용이 시간에 따라 계속 변화하는 상황을 다룸.
        - 이 '치료' 자체가 미래의 교란 변수(confounder)에 영향을 미치는 경우에 사용됨.
        - 데이터는 주로 개개인을 장기간 추적하는 종단 연구 데이터
        - 치료의 양, 종류, 또는 여부가 시간에 따라 지속적으로 조절될 때 그 효과를 추정하는 데 활용됨.

MSM은 관찰 연구에서 **시간에 따라 변하고 이전 치료에 의해 영향을 받는 교란 변수(time-dependent confounders)**가 있는 상황에서 **노출의 인과 효과**를 보다 엄밀하게 추정하기 위한 인과 모델입니다.

*   **목표** : 기존 다른 방법으로는 편향될 수 있는 '교란 변수이자 중간 변수' 역할을 하는 시간 의존적 교란 변수로 인한 편향을 해결합니다.

*   **MSM의 개념 및 주요 특징**:
    *   **Marginal (주변)**:
        *   특정 개인이나 특정 공변량 값에 **조건화하지 않고** `전체 모집단` 또는 `특정 하위 모집단` (예: 치료받은 사람) 수준에서 노출의 **평균 인과 효과**를 추정하는 것을 목표로 합니다.
        *   이는 특정 사람의 특성과 무관하게 `전체적으로` 개입이 미치는 영향을 이해하는 데 중점을 둡니다.
    *   **Structural (구조적)**:
        *   관찰된 데이터 간의 단순한 통계적 연관성을 넘어 특정 개입(`노출`)이 `결과`에 `어떻게 인과적으로 영향을 미치는지`를 설명하는 **반사실적(counterfactual) 관계**를 모델링합니다.
        *   마치 임의 할당된 실험에서처럼 특정 개입을 받았을 때(반사실)의 결과를 가정하여 인과적 메커니즘을 파악하려 합니다.

*   **주요 추정 방법**:
    1.  **Inverse-Probability-of-Treatment Weighting (IPTW)**:
        *  각 대상자에게 '자신이 받은 치료를 받을 조건부 확률의 역수'로 가중치를 부여해 마치 무작위 배정된 것처럼 교란 변수를 조정한 가상의 모집단을 만듭니다.
        *  `Propensity Score Model(성향 점수 모델)`이 정확해야 일관적입니다.
    2.  **이중 강건 (Doubly Robust) 추정 (예: LTMLE)**:
        *   `Propensity Score Model(성향 점수 모델)`과 `Delta Outcome Model(델타 결과 모델)`을 모두 사용 합니다.
        *   강건성: **두 모델 중 최소 하나만 정확해도** 일관적인 추정량을 얻을 수 있어 더 강건합니다.


* 참고 문헌
1. Li, F. (2026). STA 640 — Causal Inference: Chapter 9 – Sequential/Longitudinal Treatments [Lecture slides]. Duke University. 
2. Schomaker, M., & Baumann, P. F. M. (2023). Doubly robust estimation of average treatment effects on the treated through marginal structural models. Observational Studies, 9(3). https://doi.org/10.1353/obs.2023.0025
3. Robins, J. M., Hernán, M. A., & Brumback, B. (2000).Marginal Structural Models and Causal Inference in Epidemiology.Epidemiology, 11(5), 550–560.



* 사용 데이터 출처
ACIC Data Challenge. (2022). 2022 ACIC Data Challenge: Track 2 Practice-Level Simulated Datasets [Data set]. Mathematica & Society for Causal Inference.
https://acic2022.mathematica.org/