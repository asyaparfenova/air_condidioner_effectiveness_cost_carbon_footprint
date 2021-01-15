# How much does 1°C cost you and nature

This is my final project in SPICED Academy Data Science Bootcamp. It aims to calculate the effectiveness, cost and carbon footprint of using a portable air conditioner unit using the data from smart home sensors.
More detailed story and results of this project you can find in the [Project Presentation](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/presentation_print_format.pdf)

## Introduction

Its official title sounds pretty general, when actually it was calculating  the effectiveness, cost
and carbon footprint of using a very particular portable air conditioner unit in a very
particular apartment that belonged to my friend Sasha.

Let's look the story behind it:

![Project Inrtoduction](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/images/intro.png?raw=true)

**So, despite the abundance of raw data, some Sasha's questions remained unanswered. in particular:**
- *How hotter it would actually be in his apartment without an air conditioner?*
- *How much does it cost to cool his flat for 1°C for 1 hour?*
- *What is the carbon footprint of cooling the flat for 1°C for 1 hour?*

Obviously, a detailed data analysis and even some machine learning techniques were needed to answer them. That is how an idea of this project was born.

## Project Idea and Plan

The main challenge of the project was to predict the temperature in the flat that would remain in the room without air conditioning in the span of time when actually the room was artificially cooled. Then, by integrating the difference between predicted and real time/temperature lines, the total cooling value (units: °C×h) could be calculated.

![Project Idea](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/images/idea.png?raw=true)

By knowing the running voltage of the air conditioner, the consumed energy (kW×h) can be easily calculated (also by integration).
Dividing the cooling by the energy will give us effectiveness of the air conditioner, and with some additional data about energy price and carbon footprint of energy production the cost and then carbon footprint of cooling the flat for 1°C for 1 hour could be calculated.

The initial project plan wasn’t any different from the classical machine learning project workflow, namely:
Gathering data/Data pre-processing/Researching the model that will be best for the type of data/Training and testing the model/Evaluation

## Project Development

[Data wrangling](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/Data_Wrangling.ipynb) and [Data analysis](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/EDA.ipynb) parts are presented in the separate notebooks.

An unexpected challenge emerged when it came to splitting the data. 
The initial idea was to train the model on the temperature data for the time periods, when the air conditioner was “off” and then to re-construct the “uncooled” temperature, when it was on. But here comes the hysteresis problem: it takes time to cool down the room and, more importantly, the room stays cooler for some time after switching off the cooling and that time can not be used for training.

![Data_spliting](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/images/classification.png?raw=true)

To estimate hysteresis lag regression machine learning was used, as the time after changing the state the air conditioner, when our model can not properly predict the right state or, in other worlds, to recognize that the state was changed.

## Results

![Project ML](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/images/xgb_total.png?raw=true)

## Repository Content
- /images/ (Folder with images, used in .md files and notebooks)
- [Data Wrangling (Jupiter Notebook)](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/Data_Wrangling.ipynb)
- [EDA (Jupiter Notebook)](https://github.com/asyaparfenova/air_condidioner_effectiveness_cost_carbon_footprint/blob/main/EDA.ipynb)

Coming soon:
- ML - Classification (Jupiter Notebook)
- ML - Regression (Jupiter Notebook)




