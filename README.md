# eSC Data Analysis Project

## Project Overview
In response to the growing concern over the impact of global warming on energy demand, this data analysis project investigates potential energy usage during an exceptionally hot summer, with a specific focus on July. The client, eSC, is an energy company operating in South Carolina (and a small part of North Carolina) that supplies electricity to residential properties. With the fear that global warming could intensify electricity demand, particularly during the upcoming summer, eSC aims to prevent potential blackouts by gaining insights into energy consumption patterns.

### Key Business Questions:
1. What are the historical trends in July energy usage?
2. What is the potential energy usage during an extra hot summer?

Through a comprehensive examination of relevant data, this project aims to provide eSC with actionable insights to mitigate the risks associated with increased electricity demand and safeguard against potential blackouts.

## Data Processing
The static house data and sample weather data were saved in CSV files, while the sample energy usage file was saved in a Parquet file. The following steps were taken to process the data:

1. **Loading the Data:**
   - Loaded the `tidyverse` package to read CSV files and the `arrow` package to read Parquet files.
   - Extracted `building_id` from the static house URL and saved it into the house file directory. Similarly, extracted and saved the weather URL in the weather file directory.
   - Looped through each file for processing.

2. **Preprocessing:**
   - Generated total energy used for HVAC by summing various relevant electricity consumption fields.
   - Refined the static housing data to include only July data, removed any NA values, and updated the data frame to focus on HVAC usage.
   - Created a function `get_summary_weatherDF` to extract and add weather data for each house's location into the house's data frame.

3. **Insulation Analysis:**
   - Created a hierarchical structure for the insulation data and assessed the effectiveness of better insulation, particularly roof insulation.

4. **String Conversion:**
   - Converted strings to integers, removed irrelevant columns, and saved the processed data in CSV and Parquet formats.

## Modeling
The dataset was split into training and test sets, and three models were tested:
- **Linear Regression**
- **Support Vector Regression (SVR)**
- **Decision Tree**

Based on the RMSE scores, the Support Vector Regression model was selected as it yielded the lowest RMSE score of `0.000218305666992898`.

## Prediction and Visualization
A scenario was assumed where the temperature increases by 5 degrees over the next 10 years. This modified dataset was used with the SVR model to predict future energy usage. Predictions were scaled by the square footage of the properties.

The visualization, titled "Hourly Sum of Predicted Energy Usage," shows energy usage peaking steeply after 5:30 PM and extending until 11 PM. This insight is crucial for eSC to prepare for potential spikes in electricity demand.

## Conclusion
The analysis provides actionable insights for eSC to mitigate the risks associated with increased electricity demand. The prediction model, validated through robust processes including cross-validation and split-sample testing, offers reliable forecasts that can help eSC prepare for future energy demands.

The RMSE score of `0.000218305666992898` further supports the credibility of the model, ensuring minimal error in predictions.
