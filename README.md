# Who-Is-The-Killer 🕵️‍♂️🔎

**Αναγνώριση Προτύπων (2019–2024 Homicide Dataset)**

## GitHub

https://github.com/alexispetrou/Who-Is-The-Killer

## Ομάδα

* **Αλέξιος Πέτρου** — Π22142
* **Μαρία Αγγελετοπούλου** — Π22007
* **Φώτιος Ευθυμιάδης** — Π22044

---

## Περιγραφή

Το Τμήμα Ανθρωποκτονιών Πειραιά παρέχει dataset με **4.800 περιστατικά** (ανθρωποκτονίες & απόπειρες) για την περίοδο **2019–2024**.
Στόχος της εργασίας είναι η **πρόβλεψη του δράστη (killer_id)** για κάθε περιστατικό του **TEST** split, εντοπίζοντας διακριτούς σειριακούς δολοφόνους των οποίων η δράση είναι *ενσωματωμένη* και όχι άμεσα παρατηρήσιμη στα δεδομένα.

Η λύση περιλαμβάνει:

* διερευνητική ανάλυση δεδομένων (EDA),
* στατιστική μοντελοποίηση (MLE, πολυμεταβλητές Gaussians),
* ταξινόμηση (Bayes, Linear/Ridge, SVM, MLP),
* μείωση διάστασης (PCA),
* μη επιβλεπόμενη διερεύνηση (k-means στο latent space).

---

## Dataset (Features)

Για κάθε περιστατικό δίνονται:

* **hour_float**: ώρα εγκλήματος (δεκαδική)
* **latitude, longitude**: τοποθεσία
* **victim_age**: ηλικία θύματος
* **temp_c, humidity**: καιρικές συνθήκες
* **dist_precint_km**: απόσταση από πλησιέστερο τμήμα
* **pop_density**: πληθυσμιακή πυκνότητα περιοχής
* **weapon_code**: είδος όπλου
* **scene_type**: τύπος σκηνής
* **weather**: κατηγορία καιρού
* **vic_gender**: φύλο θύματος
* **killer_id**: ετικέτα δράστη (TRAIN/VAL μόνο)

📌 Σημείωση: Υπάρχει **class imbalance** (κυριαρχία Killer 3), που επηρεάζει μοντέλα με priors.

---

## Περιεχόμενα Εργασίας (Q1–Q8)

* **Q1:** Histograms + Gaussian fit + GMM(3)
* **Q2:** MLE ανά killer + Mahalanobis analysis
* **Q3:** Bayesian classifier
* **Q4:** Linear (Ridge) classifier
* **Q5:** SVM (RBF kernel)
* **Q6:** Multi-Layer Perceptron (MLP)
* **Q7:** PCA (scree + 3D)
* **Q8:** k-means στον PCA χώρο

---

## Results (Validation Accuracy)

| Model          | VAL Accuracy |
| -------------- | ------------ |
| Bayesian       | **90.50%**   |
| Linear / Ridge | **86.74%**   |
| SVM (RBF)      | **94.68%**   |
| MLP            | **93.11%**   |

**Takeaway:** Τα μη-γραμμικά μοντέλα (**SVM**, **MLP**) έχουν την καλύτερη γενίκευση.

---

## Δομή Project

```
Who-Is-The-Killer/
├─ Data/
│  ├─ crimes.csv
│  ├─ submission.csv
│  ├─ submissionQ8.csv
│  └─ svm_results.npy
├─ Plots/
├─ Python Notebooks/
│  ├─ Data_Exploration.ipynb
│  ├─ Q1.ipynb
│  ├─ Q2.ipynb
│  ├─ Q3.ipynb
│  ├─ Q4.ipynb
│  ├─ Q5.ipynb
│  ├─ Q6.ipynb
│  ├─ Q7.ipynb
│  └─ Q8.ipynb
└─ requirements.txt
```

---

## Installation

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
source .venv/bin/activate

pip install -r requirements.txt
```

---

## How to Run

Άνοιξε τα notebooks με Jupyter ή VS Code και εκτέλεσε με τη σειρά:

1. `Data_Exploration.ipynb`
2. `Q1.ipynb` → `Q8.ipynb`

```bash
jupyter notebook
```

---

## Outputs

* **Plots/** → οπτικοποιήσεις (histograms, hexbin, PCA, decision regions)
* **Data/submission.csv** → τελικό submission (SVM)
* **Data/submissionQ8.csv** → unsupervised προσέγγιση

---

## LLM Usage (Σύντομα)

Τα LLMs χρησιμοποιήθηκαν κυρίως για:

* βελτίωση οπτικοποιήσεων,
* κατανόηση μαθηματικού υποβάθρου.

Έγινε επίσης επαναχρησιμοποίηση ιδεών από προηγούμενα projects του repo.

---

## References

* Theodoridis & Koutroumbas — Αναγνώριση Προτύπων
* Russell & Norvig — Artificial Intelligence
* GeeksforGeeks (Bayes, SVM)
* ScienceDirect Topics — Linear Classifiers
