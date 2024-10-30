# Multi-Objective Optimization of Energy Procurement with LSTM-based Price Prediction ###

## Project Overview and Problem Statement 
Steel Manufacturing Company operates a plant in Europe,requiring an electricity supply of 1,200 MWh/Day to maintain its operations.This demand is met through a combination of sourcing from the State Electricity Grid, State Power Exchange, and the company's own captive solar power plant.
The company aims to balance its electricity procurement costs with its environmental impact, particularly focusing on carbon footprint while ensuring a minimum of 20% renewable energy utilisation in its energy mix.The objectives are:
> To predict daily average electricity prices at the Power Exchange based on historical data from 2010–2017.

> To optimize procurement costs for 2018 while ensuring a minimum 20% renewable energy in the total energy mix and tracking carbon footprint.

### Variables and Parameters
-Q_Grid: Quantity of electricity drawn from the State Electricity Grid (in MWh/day). 

-Q_Exchange: Quantity of electricity drawn from the Power Exchange (in MWh/day).

-Captive Solar: Solar plant contribution, 150 MWh/day (100% renewable, 0 EUR cost).
### Costs
-Grid Cost: 57.62 EUR/MWh 

-Exchange Cost: This cost varies and is predicted by the ML model.
### Carbon Emissions
-1 MWh of coal energy produces 0.95 metric tons of CO₂.

## Constraints 
1)Total Demand 
   - Q<sub>Grid</sub> + Q<sub>Exchange</sub> + Solar = 1200MWh
     
2)Minimum Renewable Requirement:
   - 0.15×𝑄<sub>Grid</sub> + 0.05 × 𝑄<sub>Exchange</sub>Exchange + 150 ≥ 0.2×12000

## Cost Function
### The total cost of energy procurement is:
Total Cost = Grid Cost × 𝑄<sub>Grid</sub> + Predicted Exchange Cost × 𝑄<sub>Exchange</sub>
​
### Carbon Emissions Calculation:
Carbon Emissions = 0.95 × (𝑄<sub>Grid</sub> - 0.15 × 𝑄<sub>Grid</sub>) + 0.95 × (𝑄<sub>Exchange</sub> - 0.05 × 𝑄<sub>Exchange</sub>)

## Dataset
Source: Power Exchange Data 2010-2017 [https://drive.google.com/drive/folders/1ZDLNFQgCvC7C-bARppZrs2UiZ2EC1SL0]

## Requirements
The project requires the following Python libraries:
```
pandas
numpy
tensorflow/keras
matplotlib
```

## Data Preprocessing

### Handling Outliers:
Interquartile Range (IQR) is calculated for the Price column to identify and remove outliers.
### Data Scaling:
The Price data is normalized using MinMaxScaler, scaling values between 0 and 1. 
### Sequence Creation:
sequence length (e.g., 30 days) is defined to predict the next day’s price.

## Model Architecture
#### Input Layer:
Sequences of length 30days with a single feature (price).
#### Hidden Layers
````
LSTM Layers:
The first LSTM layer consists of 100 units and It also includes a Dropout layer (0.2) to reduce overfitting.
A second LSTM layer with 56 units and another Dropout layer (0.2). 
Dense Layers:
A Dense layer with 20 units, followed by a final Dense layer with 1 unit for the output, predicting the next day’s price.
````
#### Compilation and Training:
```
The model is compiled using the Adam optimizer and Mean Squared Error (MSE) as the loss function.
The model is trained over 30 epochs with a batch size of 32.
```

## Result 
### Mean Squared Error (MSE): The model achieved an  Mean Squared Error of 0.015 








