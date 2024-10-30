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
#### The project requires the following Python libraries:
'''
pandas
numpy
tensorflow/keras
matplotlib
'''






