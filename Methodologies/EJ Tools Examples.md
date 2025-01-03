# EJ Tools Examples

## EJScreen

For a **block group (ID = 420010301011) in Adams County, PA**, here are their indicators' values and the derived index values.

### 1. Demographic Index

| Demographic Burden                         | $\% \operatorname{People \space of \space Color}$ | $\% \operatorname{Low \space Income}$ | $\% \operatorname{Limited \space English \space Speaking}$ | $\% \operatorname{Less \space Than \space High \space School \space Education}$ | $\% \operatorname{Persons \space with \space Disabilities}$ | $\% \operatorname{Low \space Life \space Expectancy}$ |
|:--------------------------|:--------------------------------:|:---------------------:|:----------------------------------------:|:-----------------------------------------------:|:---------------------------------:|:----------------------------:|
| Value$_i$                   | 0.224014                       | 0.187300           | 0.023454                               | 0.026035                                      | 0.102395                       | 0.152821                  |
| Mean                    | 0.395843                       | 0.304150           | 0.048100                               | 0.113070                                      | 0.136065                       | 0.195320                  |
| Standard Deviation (STD)| 0.315152                       | 0.213371           | 0.108136                               | 0.116900                                      | 0.062492                       | 0.040118                  |
| Z-score                 | -0.544774                      | -0.547638          | -0.227917                              | -0.744525                                     | -0.538789                      | -1.059351                 |

where $\%$ denotes "the percentage of" and $i$ denotes the ID of the block group, which is **420010301011** here.

Hence, the demographic indexes are as follow:

$$
\begin{aligned}
    \operatorname{Demographic \space Index}_i
    &= \frac{\% \operatorname{People \space of \space Color}_i + \% \operatorname{Low \space Income}_i}{2} + | \min_i \operatorname{Demographic \space Index}| \\
    &= \frac{(-0.544774) + (-0.547638)}{2} + |-1.34074|= 0.974534
\end{aligned}
$$

$$
\begin{aligned}
    \operatorname{Supplemental \space Demographic \space Index}_i
    &= \frac{\% \operatorname{Low \space Income}_i + \% \operatorname{Limited \space English \space Speaking}_i + \% \operatorname{Less \space Than \space High \space School \space Education}_i + \operatorname{\% Persons \space with \space Disabilities}_i + \% \operatorname{Low \space Life \space Expectancy}_i}{5} + |\min_i \operatorname{Supplemental \space Demographic \space Index}|\\
    &= \frac{(−0.544774) + (−0.547638) + (−0.227917) + (−0.744525) + (−0.538789) + (−1.059351)}{5} + |-1.6392| = 1.028851
\end{aligned}
$$

### 2. EJ Index

| Enviromental Burden$_j$                               | $\operatorname{Particulate \space Matter \space 2.5}$ | $\operatorname{Ozone}$ | $\operatorname{Nitrogen Dioxide \space (NO_2)}$ | $\operatorname{Diesel \space Particulate \space Matter}$ | $\operatorname{Toxic \space Releases \space to \space Air}$ | $\operatorname{Traffic \space Proximity \space and \space Volume}$ | $\operatorname{Lead \space Paint}$ | $\operatorname{Superfund \space Proximity}$ | $\operatorname{RMP \space Facility \space Proximity}$ | $\operatorname{Hazardous \space Waste \space Proximity}$ | $\operatorname{Underground \space Storage \space Tanks \space (UST) \space and \space Leaking \space UST \space (LUST)}$ | $\operatorname{Wastewater \space Discharge}$ | $\operatorname{Drinking \space Water \space Non-Compliance}$ |
|--------------------------------|:---------------------------------------------------:|:-----------------------:|:----------------------------------------------:|:-------------------------------------------------------:|:-----------------------------------------------------------:|:---------------------------------------------------------------:|:-----------------------:|:-------------------------:|:----------------------------:|:-----------------------------:|:---------------------------------------------:|:---------------------------:|:--------------------------------------:|
| Value$_i$                      | 8.364576                                            | 56.896750              | 0.100221                                       | 5.215961                                              | 819.661923                                                | 127808.941500                                               | 203                     | 0.407631                | 0                          | 0.192711                     | 0.096124                                      | 0.489382                 | 162.272611                             |
| Percentile$_i$                 | 61                                                  | 23                     | 30                                             | 23                                                    | 27                                                        | 16                                                          | 43                      | 0                       | 34                         | 9                            | 33                                           | 36                       | 0                                     |
| EJ Index$_i$                   | 59.445574                                            | 22.414282              | 29.236020                                      | 22.414282                                              | 26.312418                                                | 15.592544                                                  | 41.905001               | 0                       | 33.134156                  | 8.770806                     | 32.159622                                    | 35.182227                | 0                                     |
| Supplemental EJ Index$_i$      | 62.760011                                            | 23.663573              | 30.865530                                      | 23.663573                                              | 27.779001                                                | 16.461616                                                  | 44.240593               | 0                       | 35.021026                  | 9.259659                     | 33.952083                                    | 37.038636                | 0                                     |
| EJ Index Percentile$_i$            | 53                                                  | 25                     | 34                                             | 26                                                    | 27                                                        | 19                                                          | 40                      | 0                       | 36                         | 12                           | 37                                           | 35                       | 0                                     |
| Supplemental EJ Index Percentile$_i$ | 56                                                  | 21                     | 32                                             | 20                                                    | 24                                                        | 14                                                          | 38                      | 0                       | 34                         | 8                            | 34                                           | 34                       | 0                                     |

where
$$
\begin{aligned}
    \operatorname{EJ \space Index}_{i, j} &:= \operatorname{Demographic \space Index}_i \times \operatorname{Enviromental \space Burden \space Percentile}_{i, j}\\
    \operatorname{Supplemental \space EJ \space Index}_{i, j} &:= \operatorname{Supplemental \space Demographic \space Index}_i \times \operatorname{Enviromental \space Burden \space Percentile}_{i, j}\\
    j &\text{\space dentoes \space the \space ordinal of \space enviromenal \space burden.}
\end{aligned}
$$

### 3. EJ Area Candidate Determination

Therefore,
$$
\operatorname{isEJCandidate}_i := \bigwedge_{j} \operatorname{EJ \space Index \space Percentile}_{i, j} < 80 = \operatorname{False}
$$

which means the **block group (ID = 420010301011) in Adams County, PA** is not an EJ area candidates for further manual EJ area determination process.

## CEJST

For a **cenus tract (ID = 42001030101) in Adams County, PA** (nearby of the above block group), here are their indicators' values in different categories and the derived index values.

### 1. Climate Change

| Environmental Burden$_{j_1}$                   | $\operatorname{Expected \space Agriculture \space Loss \space Rate}$ | $\operatorname{Expected \space Building \space Loss \space Rate}$ | $\operatorname{Expected \space Population \space Loss \space Rate}$ | $\operatorname{Projected \space Flood \space Risk}$ | $\operatorname{Projected \space Wildfire \space Risk}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|:----------------------------------------------------:|:-------------------------------------------------------:|
| Value$_i$                                  | 0.1968                                                              | 0.0138                                                             | 0.0002                                                               | 6                                                    | 0                                                       |
| Percentile$_i$                             | 6                                                                   | 49                                                                  | 63                                                                    | 45                                                   | 33                                                      |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |

where $i$ denotes the ID of the census tract, which is **42001030101** here and $j_k$ denotes the ordinal of the enviromenatl burdens under this category $k$, which is $1$ (Climate Change) here and
$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 1} &:= \bigwedge_{j_1} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_1} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$
and actually
$$
\begin{aligned}
    \operatorname{Low \space Income}_i = 0.15\\
    \rightarrow \operatorname{Low \space Income \space Percentile}_i = 58
\end{aligned}
$$

### 2. Energy

| Environmental Burden$_{j_2}$                   | $\operatorname{Energy \space Cost}$ | $\operatorname{PM \space 2.5}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| Value$_i$                                  | 3                                                              | 8.52                                                             |
| Percentile$_i$                             | 68                                                                   | 48                                                                  |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 2} &= \bigwedge_{j_2} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_2} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 3. Health

| Environmental Burden$_{j_3}$                   | $\operatorname{Asthma}$ | $\operatorname{Diabetes}$ | $\operatorname{Heart \space Disease}$ | $\operatorname{Low \space Life \space Expectancy}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|:----------------------------------------------------:|
| Value$_i$                                  | 990                                                              | 1130                                                             | 640                                                               | 73.09                                                    |
| Percentile$_i$                             | 57                                                                   | 60                                                                  | 59                                                                    | 89                                                   |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 3} &= \bigwedge_{j_3} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_3} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 4. Housing

| Environmental Burden$_{j_4}$                   | $\operatorname{Historic \space Underinvestment}$ | $\operatorname{Housing \space Cost}$ | $\operatorname{Lack \space of \space Green \space Space}$ | $\operatorname{Lack \space of \space Indoor \space Plumbing}$ | $\operatorname{Lead \space Paint}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|:----------------------------------------------------:|:-------------------------------------------------------:|
| Value$_i$                                  | $\operatorname{False}$                                                              | 22                                                             | 760                                                               | 0.52                                                    | 17                                                       |
| Percentile$_i$                             | 0                                                                   | 50                                                                  | 10                                                                    | 0                                                   | 41                                                      |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_i &= \bigwedge_{j_4} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_4} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 5. Legacy Pollution

| Environmental Burden$_{j_4}$                   | $\operatorname{Abandoned \space Mine \space Land \space Present}$ | $\operatorname{Formerly \space Used \space Defense \space Site \space (FUDS) \space Present}$ | $\operatorname{Lack \space of \space Green \space Space}$ | $\operatorname{Lack \space of \space Indoor \space Plumbing}$ | $\operatorname{Lead \space Paint}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|:----------------------------------------------------:|:-------------------------------------------------------:|
| Value$_i$                                  | $\operatorname{False}$                                                              | 22                                                             | 760                                                               | 0.52                                                    | 17                                                       |
| Percentile$_i$                             | 0                                                                   | 50                                                                  | 10                                                                    | 0                                                   | 41                                                      |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                | $\operatorname{False}$                                  |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 5} &= \bigwedge_{j_5} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_5} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 6. Transportation

| Environmental Burden$_{j_5}$                   | $\operatorname{Diesel \space Particulate \space Matter}$ | $\operatorname{Transportation \space Barriers}$ | $\operatorname{Traffic \space Proximity \space and \space Volume}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|
| Value$_i$                                  | 0.17                                                              | Missing                                                             | 50.86                                                               |
| Percentile$_i$                             | 0                                                                   | 98                                                                  | 19                                                                    |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{True}$                                              | $\operatorname{False}$                                                |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 6} &= \bigwedge_{j_6} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_6} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{True}
\end{aligned}
$$

### 7. Water and Wastewater

| Environmental Burden$_{j_7}$                   | $\operatorname{Underground \space Storage \space Tanks \space and \space Releases}$ | $\operatorname{Wastewater \space Discharge}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|
| Value$_i$                                  | Missing                                                              | 0.41                                                             |
| Percentile$_i$                             | Missing                                                                   | 26                                                                  |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 7} &= \bigwedge_{j_7} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_7} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 8. Workforce Development

| Environmental Burden$_{j_8}$                   | $\operatorname{Linguistic \space Isolation}$ | $\operatorname{Low \space Median \space Income}$ | $\operatorname{Poverty}$ | $\operatorname{Unemployment}$ |
|:-------------------------------------------|:--------------------------------------------------------------------:|:-------------------------------------------------------------------:|:---------------------------------------------------------------------:|:----------------------------------------------------:|
| Value$_i$                                  | 0                                                              | 114                                                             | 16                                                               | 2                                                    |
| Percentile$_i$                             | 12                                                                   | 29                                                                  | 66                                                                    | 22                                                   |
| Percentile$_i \geq 90$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |
| Low Income Percentile$_i \geq 65$                     | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |
| $\operatorname{meetThreshold}_i$                              | $\operatorname{False}$                                              | $\operatorname{False}$                                              | $\operatorname{False}$                                                | $\operatorname{False}$                                |

Therefore,

$$
\begin{aligned}
    \operatorname{meetThreshold}_{i, 8} &= \bigwedge_{j_8} \operatorname{Enviromental \space Buden \space Percentile}_{i, j_8} \geq 90 \land \operatorname{Low \space Income \space Percentile}_i \geq 65\\
    &= \operatorname{False}
\end{aligned}
$$

### 9. EJ Area Candidate Determination

Therefore,
$$
\operatorname{isEJArea}_i := \bigwedge_{k} \operatorname{meetThreshold}_{i, k} \land \operatorname{LandinTribe}_i \land \operatorname{SurroundedbyDisadvantage}_i = \operatorname{True}
$$

where $\operatorname{LandinTribe}_i$ means whether the census tract with ID $i$ (**42001030101**) are on land within the boundaries of Federally Recognized Tribes,\
and $\operatorname{SurroundedbyDisadvantage}_i$ means whether the census tract with ID $i$ (**42001030101**) census tracts that are completely surrounded by disadvantaged communities and meet an adjusted low income threshold of **50th percentile**.

It means the **block group (ID = 420010301011) in Adams County, PA** is an EJ area.
