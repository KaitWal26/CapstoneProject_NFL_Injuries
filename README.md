# NFL Injury Capstone Group Project

## Rohan Binu, Leah Cordova, Ari Crumley, Kaitlynn Walston

### 1 Motivation
#### 1.1 Objective
The goal for this project is to develop an interactive data dashboard that identifies, models, interprets, and visualizes the different risk factors that contribute to various NFL injuries. This dashboard will include a combination of boxplots, scatter plots, heatmaps, pie charts, and drop down menus for a user to filter the results based on their interest. This project will also provide a diagnostic tool for coaches, trainers, and analysts to understand injury probability, as well as aid in development of protective measures. Users will be able to enter a series of variables and be provided an output of probability a hypothetical player will be injured within the next week.<br>
NFL injuries cost teams millions in cap space and significantly lower win probabilities. By identifying which aspects correlate with injury spikes, teams can better manage player rotation, and league officials can back safety-related rule changes with evidence. By using the interactive tool, coaches, trainers, and analysts will be able to use it as a diagnostic tool in order to understand injury probability, and as well as aid in development of protective measures. This tool can also be used by college/youth athletes and their guardians to understand the risks associated with various factors personal to them, such as position, play types, prospective colleges, coaching styles, etc.

#### 1.2 Stakeholders
The main clients for this project are the NFL League Office, NFL Front Office Analysts, Sports Medicine Coordinators, Managers & Coaches, and Team Owners. These entities provide the data used for the project and will be able to utilize the tool to make better decisions, backed by data, to prevent injuries from occurring before they take place by monitoring for increased risk factors in real time.<br>
The main beneficiaries for this project are Current and retired NFL players, NFL Medical Personnel, and Equipment Manufacturers. As current and retired NFL players can benefit from added measures to prevent and/or treat injuries, they serve as the main demographic to benefit from the development of this tool. With added knowledge of what commonly precedes injuries, NFL Medical Personnel will be able to better recognize and treat injuries as they occur on the field. Equipment Manufacturers can improve designs of protective gear to better protect players. 

#### 1.3 Related Works
W. R. Cole et al., “Neither American Football Playing Position Nor Total Years Playing Football Are Associated with Neurobehavioral Health Outcomes: An NFL-LONG Study,” Current Sports Medicine Reports, vol. 24, no. 11, pp. 372–379, Nov. 2025, doi: https://doi.org/10.1249/jsr.0000000000001300. <br>
In this study, researchers identified several risk factors associated with player injuries using variables such as game outcome (win/loss), playing surface, stadium, and temperature. While these factors provide valuable context, their scope is relatively limited. This project will build upon that foundation by incorporating more play-by-play data, including variables such as play type, player age, position, snap counts, and down. Expanding the features will allow for a more comprehensive analysis, improving the ability to detect meaningful patterns and enhancing the potential for injury prediction.<br>
“Introducing Our Multi-Year Injury Risk Model,” Sports Info Solutions, Sep. 10, 2025. https://www.sportsinfosolutions.com/2025/09/10/introducing-our-multi-year-injury-risk-model/” <br>
This prior study focused on predicting which positions or individual players were most likely to experience injuries, using games missed as the primary outcome measure. The researchers implemented an Extreme Gradient Boosting (XGBoost) model, which aligns well with the methodology for this project. Building on this foundation, this current project will incorporate more play-by-play data to support predictions within a defined window, such as estimating the likelihood that a player will miss the following week. This forward-looking approach may provide insights for stakeholders, enabling more proactive injury prevention and player management strategies.

### 2 Data Strategy and Technical Methodology
#### 2.1 Data Strategy
This project will utilize the nflreadR::load_injuries() data set for weekly reports, as well as the nflfast_load_pbp() data set for play-by-play information. The planned target variable is a binary injury indicator that states whether a player will be on the following week’s injury report. This will be achieved by looking at the multiple features in the dataset, including: play type, which down the play occurs, time remaining in the game, if the game was a playoff game or a regular season game, playing surface, temperature, weather, the player’s age, position, and what team they are on (offense,defense, or special teams).<br>
This dataset contains both structured and unstructured data elements. Text-based fields identify the injured player, their position, and the anatomical location of the injury, while numerical variables capture game conditions and situational factors. Prior to analysis, the data will require preprocessing to ensure consistency and usability. This process will include cleaning missing or inconsistent values and transforming relevant text fields into structured features where appropriate. Additionally, the injury dataset will be merged with play-by-play data to create a unified dataset that links player participation and in-game context to subsequent injury reports.<br>
Given the size of the available data, data reduction will be necessary. The analysis will focus on seasons from 2010 to 2025, a sufficiently large sample for modeling. A feature selection process will also be conducted to remove irrelevant or redundant variables and improve model performance. The dataset contains missing values that must be addressed prior to model development. Using tools from the tidyverse in R, missing data will be evaluated and handled through appropriate methods such as imputation or omission. 

#### 2.2 Technical Methodology
Injury reports, play-by-play data, and roster information will be collected using the nflreadR and nflfastR packages. Identifiers such as season, week, team, and player ID will be standardized to support dataset integration. Unstructured injury text will be transformed into structured labels, while play-by-play data will be combined to generate weekly workload features. The resulting processed dataset will serve as the foundation for predictive modeling and will additionally support the development of an interactive Shiny dashboard to visualize injury risk and patterns.<br>
A Logistic Regression model will be implemented as the baseline to estimate injury probability, initially using player position as the primary predictor. Establishing this benchmark will enable clear performance comparisons as more complex models are introduced. To capture nonlinear relationships and higher-order feature interactions, the analysis will explore methods such as Random Forests and Extreme Gradient Boosting (XGBoost). These models are well-suited for structured sports data and may provide improved predictive performance relative to the baseline.<br>
The project will be developed in R, utilizing packages including nflreadR, nflfastR, tidyverse, and data.table for data preprocessing and analysis. An interactive dashboard and predictive interface will be built using Shiny, enabling users to actively explore injury trends and model outputs.

### 3 Evaluation and Metrics
#### 3.1 Model Evaluation
Model performance will be evaluated using Area Under the Receiver Operating Characteristic Curve (AUC-ROC) to assess the model’s ability to distinguish between injured and non-injured players across multiple predictors. Because injury events are relatively infrequent and correctly identifying them is a primary objective, an F1-score will also be used to balance precision and recall. Together, these metrics provide a comprehensive assessment of classification performance while accounting for potential class imbalance.

#### 3.2 Success Criteria
Project success will be evaluated across three primary metrics: model performance, dashboard functionality, and practical utility for stakeholders.<br>
Model performance will be assessed using AUC-ROC and F1-score, with success defined as achieving well-calibrated probability estimates and demonstrating significant improvement over baseline model/s.<br>
Technical success will be measured by the reliability and interactivity of the dashboard. Users should be able to filter data by position, team, injury type, and/or season while viewing injury risk predictions and feature importance in real time without errors or excessive latency.<br>
Practical utility will be evaluated based on the dashboard’s ability to generate practical insights. The project will be considered successful if clients and beneficiaries can clearly identify factors associated with elevated injury risk and use these findings to support decisions related to player rotation, workload management, and safety strategies.



### 4 Project Management
#### 4.1 Project Roles
Project Manager/Lead - Leah Cordova: leah.cordova@colostate.edu<br>
Data Engineer - Kaitlynn Walston: kaitlynn.walston@colostate.edu<br>
Deployment/Front End - Rohan Binu: rohan.binu@colostate.edu<br>
Machine Learning Expert - Ari Crumley: ari.crumley@colostate.edu

#### 4.2 Project Timeline
The project will be completed across three structured sprints aligned with the course schedule. Initial team formation and topic selection occurred in Week 2, followed by proposal drafting in Week 3 and Week 4.<br>
Sprint 1 (Weeks 4–6): Data Preparation and Exploratory Dashboard Development<br>
During this phase, both datasets will be cleaned, merged, and prepared for analysis. Preliminary feature selection will be conducted, and early development of the Shiny dashboard will begin using raw data to create interactive visualizations. Establishing the dashboard early will support gradual improvements throughout the project.<br>
Sprint 2 (Weeks 7–10): Model Development and Predictive Tool Construction<br>
This sprint will focus on training and evaluating predictive models, including Logistic Regression, Random Forests, and XGBoost. Model outputs will later be integrated into the dashboard to support an interactive predictive tool.<br>
Sprint 3 (Weeks 11–16): Website Integration and Final Deployment<br>
The final phase will emphasize integrating and refining the interactive dashboard and website, ensuring seamless functionality between informational visualizations and predictive components. The project will conclude with this usability testing and preparation for the final presentation in Week 16.

#### 4.3 Major Risks and Contingency Plans
Risk 1: Dataset Integration Challenges<br>
Injury reports identify when players are injured but do not consistently specify the exact play associated with the injury. This creates potential challenges when merging injury data with play-by-play records and roster information. To minimize risks when merging, standardized player identifiers and temporal markers (season and week) will be used to minimize mismatches. If precise merging proves unreliable, analysis will shift toward weekly metrics rather than single-play attribution, ensuring the project methods remain sound.<br>
Risk 2: Class Imbalance Due to Rare Injury Events<br>
Injuries represent a relatively small proportion of total plays, which may bias model training and reduce predictive sensitivity. To combat this, techniques such as class weighting or threshold tuning will be strongly considered to improve model performance. Additionally, evaluation metrics such as F1-score and AUC-ROC will be prioritized over accuracy to ensure meaningful assessment.
