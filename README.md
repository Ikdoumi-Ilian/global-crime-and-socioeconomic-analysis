# Global Crime & Socioeconomic Analysis

Academic project done during my 2nd year of MIASHS at Université Paul Valéry Montpellier 3 (2024-2025), for the Databases and Data Science 2 courses.

The goal was to study whether a country's development model (economy, urbanization, geography) actually determines how safe its cities are. We crossed crime indices from 404 cities with socioeconomic indicators from 103 countries to test this statistically.

## Research question

To what extent does a country's development model influence the safety level of its cities?

We wanted to check if economic wealth is really the main driver of urban safety, or if other factors like minimum wage, unemployment or urbanization play a bigger role.

## Datasets

Both datasets come from Kaggle (2023):

- World Crime Index 2023 — 404 rows, crime indices at city level
- Global Country Information 2023 — 103 rows, GDP, minimum wage, unemployment rate, urban population and other national indicators

## Tools

- SQL (MySQL with MAMP and phpMyAdmin) for the database
- R and RStudio for the statistical analysis
- R Markdown for the final report
- ggplot2 for the visualizations
- Excel and LibreOffice Calc for the initial data cleaning

## Methodology

### Database part

We built a conceptual data model (MCD) and a relational model (MOD), imported both datasets into MySQL, and wrote SQL queries to extract the indicators we needed.

A big part of the work was the cleaning step before importing: standardizing country names, grouping US states and Canadian provinces, removing irrelevant columns, and reformatting numeric fields (removing $, %, thousand separators) so SQL could read them as proper numeric types.

### Statistical part

In R we produced a world crime map and scatter plots crossing the average crime index with GDP, minimum wage, unemployment rate and urban population. Then we ran a multiple linear regression to test whether the combination of GDP, minimum wage and unemployment had a significant effect on crime.

## Key findings

The multiple linear regression gave a Fisher statistic of F = 2.982 with a p-value of 0.036, which is below the 5% threshold. So we can say, with a 5% risk, that the combination of GDP, minimum wage and unemployment has a significant effect on a country's crime level.

But the model only explains around 10.3% of the variance (R² = 0.103), which means economic factors alone are not enough to explain insecurity. Looking at each variable individually, only the minimum wage is significant on its own (p = 0.019), with a negative coefficient of −1.23: the higher the minimum wage, the lower the crime index. Once we account for minimum wage, GDP and unemployment lose their individual significance.

Three main takeaways:

- Raw economic wealth (GDP) doesn't guarantee safety. Venezuela and South Africa are economically significant but have high crime levels, while Qatar and Switzerland combine wealth and safety.
- Minimum wage is the most relevant economic lever in our model. Countries with higher minimum wages tend to be safer.
- Massive urbanization is not automatically linked to insecurity. Big Asian cities in Japan or China stay very safe despite their density.

## Limitations

The dataset is geographically unbalanced: the United States alone is almost half of the cities studied, while Sub-Saharan Africa and Central Asia are underrepresented. The crime index is also based on perception rather than official statistics, which is a methodological limit. And with an R² of only 10%, most of the variance stays unexplained — variables like income inequality, education or public policy would probably improve the model.

## Team — AMAI Group

Ahmed Zizi, Moatacem Haki, Adem Ejebli, Ilian Ikdoumi.

## Report

The full report (in French) is available in this repository as `rapport-GAMAI.pdf`.

Project supervised by Mme Sandra Bringay (Databases) and Mme Marine Demangeot (Data Science 2).
