<h1 align='center'> ▀▄▀▄▀▄ Taxi Fare and Provider Prediction ▀▄▀▄▀▄</h1>

<p align='center'> <b>Course:</b> DS150 (Time Series Analysis) <br>
<b>Date Completed:</b> April 18, 2024  </p>

---

<h2> Project Summary </h2>
This project explores the use of machine learning and deep learning techniques within the taxi industry. Our main goals were two-fold:
<ol>
  <li> <b>Regression:</b> Predict the <i>FareAmount</i> based on ride characteristics. </li>
  <li> <b>Classification:</b> Predict the <i>Taxi Provider name</i> based on the same attributes. </li>
</ol>

<p> <br> Working with an extensive dataset (around 11.9 million rows), I had to implement chunking techniques to bypass memory limitations during data ingestion. I also performed exploratory data analysis (EDA) and data cleaning—such as calculating speed limits, filtering out impossible negative values, dropping rides that lasted over 16 hours, and capping maximum speeds at 75 mph based on real-world interstate limits. </p>

<p> I've applied both traditional machine learning (Linear Regression) and Deep Learning models to handle the predictive tasks. For the results of this project, the prediction model in Linear Regression is off by an average of $9.30 and regarding the Deep learning model, the accuracy for classification was 37%. <br> </p>

<h2> Contents of the Data </h2>
In this dataset, 7 features were retained from the 31 original columns. The dataset used for this project contains the following columns, detailing various aspects of each taxi ride:
<ol>
  <li> ID (object): A unique alphanumeric identifier for each individual taxi ride. </li>
  <li> Date (datetime64): The specific date and time the ride occurred. </li>
  <li> ProviderName (category): The name of the taxi or ride-share company providing the service (e.g., UVC, Yellow Cab). </li>
  <li> FareAmount (float64): The total cost of the ride. </li>
  <li> PaymentType (float64): A numeric representation indicating the method of payment used by the passenger (e.g., cash, credit card). </li>
  <li> Mileage (float64): The total miles or distance traveled during the trip. </li>
  <li> Duration (float64): The total minutes the trip took to complete </li>
</ol>

---

## Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Modeling:** Scikit-Learn, TensorFlow / Keras
* **Environment:** VSCode, Jupyter Notebook

---

## Lessons Learned: A 2026 Reflection

I originally completed this project back in 2024, and for a long time, I was hesitant to make it public. When evaluating the deep learning model for the fare prediction, the metric printed out an accuracy of `0.000003` (practically zero). For a while, I genuinely worried that everything I did was wrong and felt a bit embarrassed by the poor result. 

<p> Looking back at this code now in 2026, I realized logic behind the cleaning were actually solid, however, I could've cleaned the data more to remove extraneous outliers. I was also missing crucial steps in training the model and I made some labeling mistakes in the regression segment and <b> evaluated a regression problem (`FareAmount`) using a classification metric (`accuracy`). </b> Because `accuracy` expects an exact floating-point match (e.g., guessing $7.57000 instead of $7.57001), the score was virtually zero. Furthermore, when evaluated correctly using Mean Absolute Error (MAE), the model was actually converging nicely, predicting fares within a ~$6 margin of error. <br> </p> 

**Key Takeaways and Possible Revisions:**
* Always double-check the evaluation metrics and its labeling. I should've used MSE/MAE for the metrics of continuous numbers (Regression) and Accuracy/F1-Score for categories (Classification). I'd have to remove the Accuracy metric in the regression segment.
* Clean the Mileage column more; drop the rows with minutes exceeding `50 miles`, a most common mileage range of Uber drivers per day [1], assuming that most standard taxis would never drive more than the mentioned value *in a single trip*.
* Drop more rows on Duration column; particularly trips exceeding 8 hours or `480 minutes` [2], in accordance to the maximum accumulated on-duty duration of taxi drivers.
* DO Feature Importance (Random Forest, Permutation, or SHAP methods) to determine which variables are the strong predictors on my model's output.
* Need to perform Comparative Benchmarking on various models (Classification and Regression).
* Aaaaand growth in data science is a process. Revisiting the project and nitpicking the mistakes is quite refreshing.

<p> <br> I'm publishing this repo exactly as it is (warts and all) to document my journey, show my genuine problem-solving process, and highlight how much my debugging skills have grown since 2024. I'll also commit a new <b>refactored</b> file to improve the existing model in the near future (I hope I can find the original dataset ૮(◞ ‸ ◟ )ა). <br> </p>

---
References:
<p> [1] https://www.solotravellerapp.com/how-many-miles-do-uber-drivers-drive/ <br>
[2] https://www.ecfr.gov/current/title-49/subtitle-B/chapter-III/subchapter-B/part-395 </p>


<p align='center'> ▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄▀▄ </p>
