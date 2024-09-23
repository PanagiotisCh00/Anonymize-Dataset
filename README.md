# Anonymize Dataset
Project Overview

This project involves data de-identification to balance privacy and utility, ensuring that the de-identified dataset can be publicly released without compromising individuals' sensitive information. The anonymized dataset is designed for three specific use cases: educational investment, gender-based income analysis, and credit score fairness evaluation.

The project was completed as part of the Protecting Data coursework in my postgraduate studies, and it demonstrates how to implement data de-identification techniques such as k-anonymity, generalization, and clustering to protect personal privacy while maintaining the dataset's utility.
Dataset Description

The dataset provided contains 100,000 records with attributes such as:

    area: Geographic location
    postcode: Postal code
    dob: Date of birth
    gender: Gender
    name: Name of the individual
    marital_status: Marital status
    num_children: Number of children
    qualifications: Educational qualifications
    occupation: Occupation
    income: Yearly income
    on_benefits: Whether the individual receives benefits
    home_ownership: Homeownership status
    credit_score: Credit score

Use Cases

The anonymized dataset is intended to be used for:

    Educational Investment: Identifying locations where poor access to education leads to deprivation.
    Income Analysis: Analyzing the impact of gender on income distribution.
    Credit Score Fairness: Investigating the fairness and bias in credit score algorithms.

Methodology
1. Initial Steps

    Removed Identifiable Information: Removed columns such as name, dob, and postcode that could uniquely identify individuals.
    Analyzed Distribution: Utilized histograms and bar charts to analyze numerical and categorical columns, guiding the de-identification process while preserving utility.

2. Data Grouping and Generalization

    Age Grouping: Divided age into six distinct groups to maintain privacy without removing records, ensuring utility for credit score analysis.
    Number of Children: Reduced the uniqueness of individuals with larger families by grouping num_children into four categories (0, 1, 2-3, 4-9).
    Income Grouping: Segmented income into £5000 ranges to preserve differences in gender-based income disparities while protecting privacy.
    Credit Score Grouping: Grouped credit_score using the Experian scale, ensuring compatibility with industry standards while protecting sensitive information.

3. Clustering and Attribute Merging

    Clustering Areas: Used the K-means algorithm to cluster areas into 10 groups, preserving similarities between qualifications and area distribution.
    Clustering Occupations: Clustered occupations based on income distributions to ensure utility in income-related use cases.
    Attribute Merging: Merged less frequent education categories (Other and Apprenticeship) and removed the marital_status attribute after confirming it had no significant impact on credit score predictions.

4. Achieving 6-Anonymity

Tested various k-values and selected k=6 for achieving 6-anonymity, ensuring that each individual in the dataset is indistinguishable from at least five others. Approximately 90% of the original dataset was retained after applying de-identification techniques.
Privacy and Utility Guarantees

    6-Anonymity: Ensured that no individual can be distinguished from fewer than five others based on quasi-identifiers.
    Utility Preservation: The dataset remains useful for all three use cases, with minimal impact on data distribution or statistical properties, as confirmed by comparing the dataset before and after record removal.
    Risks: While the dataset maintains 6-anonymity, it remains vulnerable to homogeneity and semantic attacks due to the lack of l-diversity.

    Privacy Level: Measured using metrics such as k-anonymity and the risk of re-identification.
    Utility Loss: Evaluated by comparing the results of machine learning models and statistical analysis on the original and anonymized datasets. For example, assessing the accuracy of predictions in the income analysis and biases in the credit_score algorithm.

This project was developed as part of the Privacy Engineering course (EPL133) at the Imperial College London.
