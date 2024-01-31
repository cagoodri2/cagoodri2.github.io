---
layout: default
---

## Life Expectancy & Global Metrics for Health - Advanced Analysis ##

_Executive Summary_

This executive summary highlights my personal contributions to a team project. 

__Overview__

Global health inequalities contribute to both the kinds of health problems individuals face & an individual’s resilience to these challenges. Advanced analysis of public health data helps reveal important information
about the challenges a population faces. In turn, this could illuminate potential novel public health interventions or reinforce the need for current practices. This project utilized a dataset from both the World Health Organization & the World Bank. There were a total of 32 variables investigating both societal and health factors for 179 countries. The features included a broad set of metrics like GDP, sanitation levels and specific vaccination rates for common diseases (among others). 

__Problem Summary__

Linear Discriminant Analysis (LDA) was applied to predict the region a country belonged to as well as to explore the defining health characteristics used to differentiate the regions. **Add info for how LDA functions**

__Solution Summary__

The initial data exploration involved a distribution summary for all variables, a correlation matrix, an initial linear regression, and forward regression. Linear Discriminant Analysis (LDA) was then applied for geometric method vs. statistical (PFA) approach to examine the differences between regions. The five regions were Africa, Americas, Asia, Europe, and Oceania. LDA was able to predict the five regions with 83.7% accuracy (test). The first two linear discriminants accounted for 80% of the seperation. Primary contributors of Linear Discriminants for LD1 was Alcohol & Thinness. Primary contributions for LD2 were thinness, HIV/AIDS, Measles & Life
Expectancy. 

__Conclusions & Future Work__
LDA was able to successfully identify data based on region with a degree of accuracy (83.7%). Focusing solely on a region when developing public health responses may be missing important interactions and
relationships globally. These results underscore the global nature of public health problems - to truly address health inequalities, region or disease specific interventions may be limited. Reinforcing more recent calls by domain experts to engage with structural inequalities (1,2)

1) 3. Brown, A. F., Ma, G. X., Miranda, J., Eng, E., Castille, D., Brockie, T., Jones, P., Airhihenbuwa, C.
O., Farhat, T., Zhu, L., & Trinh-Shevrin, C. (2019). Structural Interventions to Reduce and Eliminate
Health Disparities. American journal of public health, 109(S1), S72–S78. https://doi.org/10.2105/AJPH.2018.304844

2) Frieden T. R. (2010). A framework for public health action: the health impact pyramid. American
journal of public health, 100(4), 590–595. https://doi.org/10.2105/AJPH.2009.185652

[Sample R Code](./who_rcode.html)

[Technical Report Sample](./who_tech.html)

[All Projects](./)
