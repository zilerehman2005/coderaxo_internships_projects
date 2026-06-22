**Insights Report: Exploratory Data Analysis of the Titanic Dataset**

# 1. Dataset Overview

The Titanic dataset is drawn from the passenger manifest of the RMS
Titanic, which sank in the North Atlantic in April 1912 after striking
an iceberg. Of the roughly 2,224 people on board, more than 1,500 died,
making it one of the deadliest maritime disasters in history. The
version used here, loaded through Seaborn, contains 891 passenger
records and is a standard benchmark dataset for binary classification
tasks.

Each row represents one passenger, with columns describing demographics
(age, sex), ticket and cabin details (class, fare, deck), family
relationships aboard (sibsp, parch), and the survival outcome. The
dataset mixes numeric features (age, fare, sibsp, parch) with
categorical features (sex, embarked, class, who, deck) and a binary
target (survived).

# 2. Key Findings: Features Correlated with Survival

The correlation heatmap (Figure 6) together with the supporting plots
highlights which features are most strongly tied to survival.

-   Pclass (r ≈ −0.34): the strongest numeric correlation. Survival
    dropped as passenger class number increased, meaning Third Class
    passengers fared worst (Figure 3).

-   Fare (r ≈ 0.26): positively correlated with survival, largely
    because higher fares are associated with First Class tickets (Figure
    5).

-   Age (r ≈ −0.07) and Parch (r ≈ 0.08): both very weak, not reliable
    predictors on their own.

-   Sex: not part of the numeric heatmap, but the strongest predictor
    overall. Female passengers survived at roughly 74%, compared to
    roughly 19% for male passengers (Figure 7), consistent with the
    historical evacuation priority given to women and children.

# 3. Supporting Observations

## Survival and class

Figure 3 shows First Class had more survivors than non-survivors, Second
Class was close to even, and Third Class was overwhelmingly
non-survivors. This matches the historical detail that Third Class
cabins were located lower in the ship, further from the lifeboats.

## Fare and outliers

Figure 5 shows First Class fares are widely spread with a few extreme
outliers above 500, while Second and Third Class fares sit in a narrow,
low range. Figure 4 shows higher-fare passengers tended to survive
regardless of age, reinforcing the fare-survival relationship seen in
the correlation heatmap.

## Age distribution

Figure 2 is right-skewed, with most passengers in their 20s and 30s and
a long tail toward older ages. The sharp spike around age 30 is partly
an artefact of mean imputation used to fill missing age values.

## Missing data

Figure 1 shows deck is missing for the majority of records, age is
missing for a meaningful portion, and embarked/embark_town are missing
for only a few rows. The scale of missingness in deck makes simple
imputation unreliable for that column.

# 4. Conclusion

Survival on the Titanic was driven primarily by sex and passenger class,
with fare contributing a secondary, overlapping signal tied to
socioeconomic status. Age, sibsp, and parch show weak individual
correlations but may still add value when combined with stronger
features.

For future model development, sex, pclass, and fare appear to be the
most useful predictors, with age, sibsp, and parch as supporting
features. Before modelling, categorical variables should be encoded
numerically, age imputation should move beyond a simple mean (for
example, grouped by pclass and sex), fare should be scaled or
log-transformed to manage skew and outliers, and deck should either be
dropped or treated as its own missing-value category rather than imputed
normally.

# Visual References




*Figure 3. Survival counts by passenger class.*

<img width="450" height="305" alt="image" src="https://github.com/user-attachments/assets/ade739d8-161f-40f4-94db-cb2488af9dfb" />

*Figure 7. Survival rate by sex.*

<img width="450" height="298" alt="image" src="https://github.com/user-attachments/assets/dbc396a4-d8b6-4edb-984c-c4dc7c2df372" />


*Figure 6. Correlation heatmap of numeric features.*

<img width="509" height="347" alt="image" src="https://github.com/user-attachments/assets/3961b8f9-342f-4a69-be3c-45c5cdedbf6d" />


*Figure 5. Fare distribution by passenger class.*

<img width="450" height="306" alt="image" src="https://github.com/user-attachments/assets/9c4b81fd-8843-41fe-a365-d47c13c46289" />


*Figure 2. Age distribution of passengers.*

<img width="450" height="300" alt="image" src="https://github.com/user-attachments/assets/dd2c4030-29de-4703-82a5-d2bcf3682bbe" />


*Figure 4. Age vs fare, coloured by survival.*

<img width="509" height="328" alt="image" src="https://github.com/user-attachments/assets/e12eada8-d73b-4578-b5fb-2507dee0fd6d" />


*Figure 1. Missing values heatmap across all columns.*
<img width="420" height="403" alt="image" src="https://github.com/user-attachments/assets/f2afcf01-23e6-457e-a35c-4810845240ab" />

