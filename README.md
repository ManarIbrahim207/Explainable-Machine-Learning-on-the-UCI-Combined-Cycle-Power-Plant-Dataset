# **Explainable Machine Learning on the UCI Combined Cycle Power Plant Dataset**

This repository contains the full implementation and report for an explainable machine learning project combining a **small‑scale literature review** with a **hands‑on implementation** of SHAP and LIME on a real‑world regression dataset.

The project investigates how modern XAI (Explainable AI) techniques can provide transparent, human‑interpretable explanations for predictive models, especially in industrial and environmental settings.

---

## **📌 Project Overview**

Machine learning models often achieve high accuracy but operate as “black boxes,” making it difficult to understand *why* they make certain predictions.  
This project explores:

- How explainable ML techniques (SHAP & LIME) are used in recent research  
- How these techniques behave when applied to a real regression problem  
- Whether explanations align with domain knowledge (power‑plant physics)  
- How model complexity affects interpretability  

The study uses the **Combined Cycle Power Plant (CCPP)** dataset from the UCI Machine Learning Repository to predict net hourly electrical output based on ambient conditions.

---

## **📂 Repository Structure**

```
📁 project-root
│
├── 📄 ICT202-Assignment1-Report.docx     # Final written report
├── 📄 assignment1.py                      # Python code (clean, commented)
├── 📄 README.md                           # This file
└── 📁 figures/                            # SHAP, LIME, and model evaluation plots
```

---

## **🧵 Dataset**

**Source:** UCI Machine Learning Repository  
**Dataset:** Combined Cycle Power Plant (CCPP)  
**Size:** 9,568 hourly observations  
**Features:**
- AT — Ambient Temperature  
- V — Exhaust Vacuum  
- AP — Ambient Pressure  
- RH — Relative Humidity  
- PE — Net Electrical Output (target)

The dataset is ideal for explainability because:

- All features are continuous  
- Physical relationships are well‑understood  
- Nonlinear effects are expected  
- Explanations can be validated against domain theory  

---

## **📚 Part 1 — Small‑Scale Literature Review**

The report reviews **five peer‑reviewed journal articles (2020–2025)** applying SHAP, LIME, or related XAI methods to predictive modelling tasks in:

- Geoscience  
- Agriculture  
- Water quality monitoring  
- Industrial fault diagnosis  
- Epidemiology  

### **Key insights from the literature:**

- SHAP is widely used for **global + local** explanations in tree‑based models  
- LIME provides **instance‑level** interpretability using local surrogate models  
- XAI improves trust, feature selection, and model validation  
- Many studies lack:
  - explanation stability analysis  
  - cross‑validation of feature importance  
  - robustness checks  
- SHAP and LIME often align with domain knowledge, strengthening credibility  

These findings motivated the experimental design for this project.

---

## **🧪 Part 2 — Experimental Design**

### **Models Implemented**
- **Random Forest Regressor** (primary model)  
- **Linear Regression** (baseline)

### **Pipeline**
1. Load dataset  
2. Train/test split (70/30)  
3. Hyperparameter tuning (Random Forest)  
4. Model evaluation (MAE, RMSE, R²)  
5. Explainability analysis using:
   - **TreeSHAP** (global + local)
   - **LIME** (local surrogate models)

### **Why SHAP + LIME?**
| Aspect | SHAP | LIME |
|--------|------|------|
| Scope | Global + Local | Local |
| Model dependence | Tree‑specific | Model‑agnostic |
| Strength | Theoretically grounded | Human‑readable rules |
| Limitation | Sensitive to correlations | Sensitive to neighborhood sampling |

Using both provides complementary insights.

---

## **📊 Results**

### **Predictive Performance**
- **Random Forest:**  
  - R² ≈ **0.963**  
  - MAE ≈ **2.26**  
  - RMSE ≈ **3.28**  
- **Linear Regression:**  
  - R² ≈ **0.84**

The Random Forest captures nonlinear relationships extremely well.

---

## **🧠 Explainability Findings**

### **SHAP (Global Insights)**
- **Ambient Temperature (AT)** and **Exhaust Vacuum (V)** are the dominant drivers of power output  
- High AT and high V → **lower** predicted output  
- Effects match real power‑plant thermodynamics  
- Nonlinear thresholds appear around:
  - AT > mid‑20s °C  
  - V > ~66 kPa  

### **LIME (Local Insights)**
- Provides per‑instance explanations  
- Shows how specific feature values push predictions up or down  
- Local rules align with SHAP’s global patterns  
- Useful for operator‑level decision support  

---

## **📝 Key Takeaways**

- Random Forest provides strong predictive accuracy for power‑plant output  
- SHAP and LIME offer consistent, physically meaningful explanations  
- XAI helps validate model logic and supports trust in predictions  
- Both methods have limitations:
  - correlation sensitivity  
  - non‑causal explanations  
  - dataset‑specific patterns  

---

## **🚀 Future Work**

Potential extensions include:

- Testing additional models (XGBoost, LightGBM, neural networks)  
- Comparing SHAP/LIME with other XAI methods (e.g., Anchors, Integrated Gradients)  
- Robustness checks under noise or distribution shifts  
- Applying the pipeline to other industrial datasets  
- Conducting stability analysis of explanations  

---

## **📚 References**

All references are included in the report using **IEEE style**.

---

## **👤 Author**

**Manar Ibrahim**  
Murdoch University Dubai  
ICT202 – Machine Learning  

Just tell me what style you want.
