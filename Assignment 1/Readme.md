Bradley Kai

---

CIDM 6395
FA 2025
Assignment 1

I have learned a lot over the course of the Computer Information Systems and Business Analytics program. I have developed a foundation in Data Analytics with skills I am most confident in:

---

# Areas I am most confident in

* **Python, Google Collab & Jupyter Notebook**: I've change confidence in writing code for data analysis and visualization. Jupyter and Google Collab have been my primary environments for coding and documentation. These entire assignment was initially created in Google Collab because I am very comfortable in using this environment.

* **NymPy & Pandas**: I've become more proficient in manipulating arrays and dataframes, performing statistical operations and transforming datasets for analysis. Much of the learning and research the help build the proficiency came from sites like Datacamp.com and https://pandas.pydata.org/. These resources made it possible to execute the creation of masks in queries.

---
```python
# create a mask for Sports Cars
SCarsMask = [n for n in CarData.loc[:,'Sports Car?'] == 1]
found1 = np.where(SCarsMask)
i = found1[0]

# pipe info into a variable query1
query1 = CarData.iloc[i,:]

# create mask for Horsepower count equal or greater than 350
query2 = CarData['Horsepower'].iloc[i] >= 350
found2 = np.where(query2)
ii = found2[0].tolist()
query1.iloc[ii]

# set mask query to SportsCars variable
SportCars = query1.iloc[ii]
````

-----

* **Data ETL**: I've gained hands-on experience in extracting data from APIs and databases while cleaning and transforming it then loading it. A favorite of mine was using filters on a DataFrame to get specific pieces of data to present in graphs.

-----

```python
# put your code here
# Filter the df
jimmy_fallon_data = content_counts[content_counts['author'] == 'jimmyfallon'].copy()

# Format date for plot
jimmy_fallon_data['date_time'] = pd.to_datetime(jimmy_fallon_data['date_time'])

# Plot graph
fig = px.line(jimmy_fallon_data, x='date_time', y='content_count', title='Number of Posts by Jimmy Fallon per Day')

# Add labels
fig.update_layout(xaxis_title='Date', yaxis_title='Number of Posts')

# Show
fig.show()
```

-----

* **Visualization Foundation & Techniques**: I've been able to create meaningful visualizations using **Matplotlib** and **Streamlit**. I understand how to design visuals that commucate insights. The heavy usage of Matplotlib required research on https://matplotlib.org/ and other resources on the internet so that I could deliver specific results requested in assignments as displayed in the working piece of code below.

-----

```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```

-----

```python
url = '[https://raw.githubusercontent.com/BradBKaiBuffs/Capstone/refs/heads/main/Assignment%201/carsData.dat](https://raw.githubusercontent.com/BradBKaiBuffs/Capstone/refs/heads/main/Assignment%201/carsData.dat)'
CarData = pd.read_fwf(url, na_values = '*', header=None)

cNames = ["Vehicle Name", "Sports Car?", "Sport Utility Vehicle?","Wagon?" ,"Minivan?" ,"Pickup?","All-Wheel Drive?" ,
          "Rear-Wheel Drive?","Suggested Retail Price", "Dealer Cost" ,"Engine Size" ,"Number of Cylinders","Horsepower",
          "City Miles Per Gallon", "Highway Miles Per Gallon", "Weight", "Wheel Base" ,"Length" , "Width"]
CarData.columns=cNames

# create a mask for Sports Cars
SCarsMask = [n for n in CarData.loc[:,'Sports Car?'] == 1]
found1 = np.where(SCarsMask)
i = found1[0]

# pipe info into a variable query1
query1 = CarData.iloc[i,:]

# create mask for Horsepower count equal or greater than 350
query2 = CarData['Horsepower'].iloc[i] >= 350
found2 = np.where(query2)
ii = found2[0].tolist()
query1.iloc[ii]

# set mask query to SportsCars variable
SportCars = query1.iloc[ii]

# Replacing Nan values in 'City Miles Per Gallon' with the City min value above
# Replacing Nan values in 'Highway Miles Per Gallon' with the Highway MPG min value above
# did it this way since I thought it was more efficient to put in the code
valuesMPG = {'City Miles Per Gallon': 13.0,'Highway Miles Per Gallon': 19.0}
SportCars = SportCars.fillna(value = valuesMPG)

#Now remove all columns which have 0's in all values
# finds columns with the sum of zero
findZeros = (SportCars == 0).all(0)

# drops columns with the zeros
SportCars = SportCars.drop(['Sport Utility Vehicle?','Wagon?','Minivan?','Pickup?','All-Wheel Drive?'], axis = 1)

#created new column from normalized [0-1] 'City Miles Per Gallon' column

# set varibles minv and maxv to locate
minv = SportCars.describe().loc['min','City Miles Per Gallon']
maxv = SportCars.describe().loc['max','City Miles Per Gallon']

# normalize values
normalizedValues = (SportCars.loc[:,'City Miles Per Gallon']-minv)/(maxv-minv)

# create new column with normalized values added
SportCars['ScaledCityMPG'] = normalizedValues

# plot figure size to 10x4
plt.figure(figsize=(10,4))

# sort for ascending order
# use different variable for array
arrayUnsorted = SportCars
# sort City MPG
arraySorted = arrayUnsorted.sort_values('City Miles Per Gallon')

# recreate an array named mpgColor1 but used 40 colors instead of 50 using the Greens colormap to match
# example and map the colors to the values of arraySorted scaledCityMPG column
cmp = plt.cm.get_cmap('Greens',40)
mpgColors1 = cmp(arraySorted['ScaledCityMPG'])

# list of integers equal to count of available names set to x-axis
carAxis = np.arange(1,10,1)
# car names
carNames = arraySorted['Vehicle Name']

# City Mpg set to y-axis
mpgAxis = arraySorted['City Miles Per Gallon']

# space between columns to be 30%
barWidth = 0.7

# use .bar(_ method
# set edge color of bars as Green and inside color from the colors mpgColors
plt.bar(carAxis, mpgAxis, width = barWidth, color=mpgColors1, edgecolor='green', align="edge")

# x-axis ticks label as car names, middle of the bars and rotate the tickets labels 90 degrees
tickLocations = carAxis+barWidth/2
plt.xticks(tickLocations, carNames, rotation = 90)
#plt.yticks(range(len(sortedMPG)), sortedCars)

# x-axis label as "Sport car make and model" and y-axis label as "City MPG"
# and plot title as "City MPG: Sport cars with 350 or more Horsepower"
plt.title("City MPG: Sport cars with 350 or more Horsepower")
plt.xlabel("Sport car make and model")
plt.ylabel("City MPG")

#show chart
plt.show()
```

-----

  * **AI & LLM API Integration**: I became familiar with large language models via APIs to explore the utilization of models. I leveraged https://ai.google.dev/api for documentation and ideas on what was needed. These actions led me to creating code and prompts to specific results like below. Additional learning was required to create a API registration key to replace the expired version. This key should last until December 7, 2025.

-----

```python
# url of the target image, please extract text from this image.
image_path="[https://github.com/czhangwt/CIDM4310/blob/main/testocr.png?raw=true](https://github.com/czhangwt/CIDM4310/blob/main/testocr.png?raw=true)"

# Declare the model name to be used
my_model_name = "gemini-2.0-flash"

# Declare the API key for authentication (embed source key for demo purpose only)
my_api_key = "AIzaSyC740KAG7DAS4StN4qQFnedknDEAUOsHyo"

from google import genai
from google.genai import types

import requests

#Requires image_path from above cell
image_bytes = requests.get(image_path).content
image = types.Part.from_bytes(
    data=image_bytes, mime_type="image/jpeg"
)
#Requires my_api_key from above cell
client = genai.Client(api_key=my_api_key)

#Requires my_model_namefrom above cell
response = client.models.generate_content(
    model=my_model_name,
    contents=["Print out the image words and put Bradley Kai at the end of the image", image],
)

print(response.text)
```

-----

# Areas I am less confident in

Even with the examples above, I have found there are areas where I still can improve a lot in. These are the areas I believe I am weak in and still provide opportunities for growth:

  * **Slicing (Advanced)**: While basic Python slicing with lists is understood, I have less experience with more powerful and performance-oriented slicing capabilities, particuarly with multi-dimensional arrays and DataFrames.
  * **Statistics**: My current understanding of statistics is based on foundational knowledge and I feel I will need a deeper and more practical understanding of statistical concepts and their application in data analysis.
  * **Python**: I have basic and working knowledge of Python but I feel I need more experience for building production-ready code. Some areas I would like to get better at is object-oriented programming, creating robust functions and writing modular, elegant code.
  * **Artificial Intelligence and LLM API**: I have a basic understanding of these concepts. My expertise is lacking in advanced prompt engineering and integration into analytical pipelines.

-----

# What I wish I knew

The following areas are skillsets and knowledge that I have not been exposed to that I think might be critical for future work:

  * **Big Data Tools & Cloud Platforms**: My experience is limited to smaller datasets that can be handled on a small scale. I would like to gain experience in distributed systems like Apache Spark, Hadoop and leverage cloud analytic platforms like AWS and Google Cloud for processing massive datasets.
  * **Production Deployment**: I have little to no experience in deploying models to production environments using tools like Docker, CI/CD pipelines and cloud services.
  * **Advanced Visualization Tools**: I have little to no experience with more advanced or complex visualization libraries like Plotly or D3.js.
  * **Real-Time Analytics**: I have a gap in knowledge regarding tools and techniques for real-time data streaming and analytics using platforms like Apache Kafka or Flink.

-----

# Summary statement of capabilities, competencies and preparedness

With all of the work above, I was able to learn, synthesize and display my knowledge in assignments that can be applicable to real-world situations at a company. I am aware that the assignments in the courses are not production-grade level, complexity-wise, so I will need additional research to produce workable code. The assignments in these courses were definitely confidence builders and created moments where I developed the mentality that the answers will not always be easy and requires resources not readily presented to me. The use of official websites with documentation and sample code helped me hurdle over challenges I faced.

-----

# Prepardness for portfolio and prototype representative project

Based on the code examples in this assignment, I have developed skills in data handling with **pandas** and **numpy**, data visualization with **matplotlib** and **plotly**, and basic **AI/LLM API integration**. These skills can be applicable to building my capstone portfolio and prototype project. Furthermore, I have sought external resources like Datacamp, pandas.pydata.org, and matplotlib.org to build an understanding of the material. I am fully aware that I need to grow more to become an efficient and effective coder but I am confident in my ability to apply learned concepts and troubleshoot with documentation. I believe this will benefit as it helps my prepardness for developing projects.

-----

# How Data Analytics integrates

  * **Data Management** is integrated through ETL processes and data cleaning which are foundational to analytics. My work with Pandas and SQL bridges the two.
  * **Software Systems** is integrated through analytics models which are embedded into applications to facilitate decision-making and enhance user experience. My work with Streamlit apps demonstrate this integration.
  * **Network and Cybersecurity** is integrated by leveraging analytics to help detect anomalies, predict threats and optimize network performance.

For my previous work, I have relied on data analytics to drive insight. Whether through visualizing trends or working with AI, Data Analytics has been the fabric connecting my work.

-----

# Data Analytics Statement

Data Analytics is not simply just a tool but rather it is a connective piece that weaves into software systems, data management and network and security into useable, real-world solutions.
