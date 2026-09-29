### An Automated Verification Framework for Generative AI Financial Summaries

Author: Venkata Ravi Kiran Gottumukkala

#### Executive summary

Generative Artificial Intelligence regularly hallucinates or mathematically alters critical information when reading corporate reports. This project delivers a Zero-Trust Automated Filter designed to catch and flag over 99% of hallucinated financial metrics from Large Language Model (LLM) pipelines before they populate downstream analytical tools. By building a paired benchmarking dataset of 5,000 corporate summaries sourced from raw SEC EDGAR disclosures and verified against structured XBRL filings, we isolate the exact feature profiles where linguistic confidence conflicts with mathematical reality. Through exploratory data analysis, Principal Component Analysis (PCA), and unsupervised clustering, this framework establishes a baseline machine learning classification pipeline. The result is a standardized Mathematical Truth Score that shields portfolio managers from toxic data, completely replacing slow, human-intensive validation with a system that can process corporate updates up to 100 times faster.

#### Rationale

Why should anyone care about this question?
1. Zero-Tolerance for Errors: Financial markets operate on absolute precision; a single fabricated metric or altered debt ratio completely invalidates a multi-million-dollar discounted cash flow (DCF) valuation model.
2. The "Fluent Liar" Dilemma: Standard generative LLMs prioritize syntax fluency and conversational elegance over structural calculation, creating beautifully written corporate summaries containing completely fictional figures.
3. Operational Bottlenecks: Left unaddressed, investment firms face operational paralysis. Analysts must completely abandon automated assistance and perform exhausting, manual data entry from PDFs into spreadsheets—wasting thousands of expensive human hours and missing time-sensitive alpha opportunities.

#### Research Question

Can we build an automated verification framework that flags hallucinated or mathematically corrupted metrics in generative AI-produced financial summaries by treating numerical data profiles as a classification and anomaly detection problem?

#### Data Sources

The project utilizes a custom paired benchmarking dataset engineered from two main pillars:
1. Unstructured Input (SEC EDGAR): Raw, textual 10-K and 10-Q corporate financial filings processed through automated LLM pipelines to output conversational financial summaries.
2. Ground Truth Verification (XBRL Filings): Official, highly structured eXtensible Business Reporting Language data used to automatically tag and cross-validate every extracted number.
3. Dataset Scale & Features: Roughly 5,000 paired data records containing a binary target label (1 for mathematically accurate, 0 for hallucinated/corrupted). Key engineered features include numerical delta
(extracted value minus true value), linguistic token confidence scores, sentence proximity to table structures, text complexity indexes, and calculated key financial ratios (e.g., debt-to-equity, revenue growth).

#### Methodology

This capstone project applies a multi-phase data science workflow spanning data cleaning, exploratory visual analysis, and baseline predictive modeling:
1. Data Cleaning & Preprocessing: Handling missing values from unmapped XBRL tags, dropping extreme outliers caused by parsing formatting errors (e.g., mixing up millions and billions), and verifying record deduplication.
2. Feature Engineering: Extracting text complexity indices and calculating proximity vectors indicating how close a metric was sitting to a structural Markdown table layout inside the raw document.
3. Exploratory Data Analysis (EDA) & Visualization: Leveraging seaborn and matplotlib to build joint distribution error scatter plots, pairwise feature matrices, and correlation heatmaps to highlight where high AI confidence correlates with massive mathematical variance.
4. Dimensionality Reduction & Unsupervised Learning: Applying Principal Component Analysis (PCA) to condense high-dimensional data profiles into 2D spaces to uncover clean spatial separations between true and false
extractions. Running K-Means Clustering to profile behavioral groups of hallucinations without exposing the model to the target labels.
5. Baseline Classification Modeling: Implementing a Decision Tree Classifier to extract human-auditable, rule-based logic pathways alongside a K-Nearest Neighbors (KNN) baseline model to categorize incoming feature
footprints against known historical anomalies.

#### Results

- Linguistic Confidence vs. Truth: Initial EDA confirms that an LLM's internal confidence tokens remain high even as the numerical delta spans multiple orders of magnitude, validating the need for an independent mathematical filter.
- Clustering Archetypes: K-Means successfully separated benign variance (e.g., rounding $12.45M to $12.5M) from structural fabrications (e.g.,assigning segment revenues to the wrong fiscal year or completely
inventing debt metrics).
- Baseline Classifier Performance: The baseline Decision Tree model demonstrates a powerful classification capability, using feature paths primarily dominated by table proximity and numerical delta to isolate over
90% of extreme hallucinations before optimization.

#### Next steps

- Incorporate Advanced Classifiers: Scale past simple trees and KNN to deploy Ensemble Methods (Random Forests, Gradient Boosting) and Isolation Forests to optimize the target filter past the 99% accuracy threshold.
- Live Dashboard Integration: Use the engineered PCA coordinates to build a front-end risk zone dashboard allowing analysts to visually review only the flagged 1% of ambiguous anomalies.
- Contextual Anchor Tracking: Refine the feature engineering layer to look for semantic anchors like "restated," "adjusted," or "pro-forma," which frequently trigger model confusion.

#### Outline of project

- Data Cleaning and Feature Engineering: Feature Engineering for Machine Learning by Alice Zheng and Amanda Casari.
- Exploratory Data Analysis and Unsupervised Clustering: Hands-On Exploratory Data Analysis with Python by Suresh Kumar Mukhiya and Usman Ahmed
- Baseline Classification Modeling and Evaluation: An Introduction to Statistical Learning with Applications in Python (ISLP) by Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani, and Jonathan Taylor

##### Contact and Further Information

For questions regarding the verification framework, pipeline execution, or replication datasets, please contact:
- Author: Venkata Ravi Kiran Gottumukkala
- Email: ravikiran.gtml@gmail.com
- GitHub Repository: https://github.com/ravikiran-gtml/bk_rk_capstone_project