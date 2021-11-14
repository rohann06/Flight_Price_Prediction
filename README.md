# Flight_Price_Prediction

#### ➡️ This machine learning model predict the price of the Flight ticket using some parameters

## 👉 Parameters
#### 1⃣ Airline name 
#### 1⃣ Source city
#### 1⃣ destination city
#### 1⃣ departure Time & Date
#### 1⃣ Arival Time & Date

<br>

## 👉 About Data :-

#### ➡️ The Data was collected from the <a href="https://www.kaggle.com/nikhilmittal/flight-fare-prediction-mh/">Kaggle</a>.
#### ➡️ There are 2 xlsx files for train data & test data.
#### ➡️ The train dataset contain 11 columns and 10.7k rows and the test dataset contains 10 columns and 2k rows.

<br>

## 👉 Data Cleaning :-
#### 🔶 As a 1st stap of data cleaning I've performed the shorting on columns like "Airline", "Source". "Destination" of  both datastes in <a href="https://docs.google.com/spreadsheets/d/1o-7FhCs56fJf07h9PSBM2y5abIVCALyo1uTFCNdhfK4/edit#gid=64045463"> google sheet </a>.

![shorting](https://user-images.githubusercontent.com/75326769/141683825-c151a7ca-aaa4-4ccb-990e-7182936782fe.png)

#### 🔶 After that, there is an airline named "Jet airways" & "Jet airways Business" which is no longer in india so we don't need that data, for that I followed the below steps...

<br>
 
#### 🔹 step 1 :  Select the column and Create the filter, in a filter select the Jet Airway and Jet Airway Business and clock OK.

![filter1](https://user-images.githubusercontent.com/75326769/141692819-21166277-8e30-432e-92eb-82e83dee4c1c.png)

#### 🔹 step 2 :  After click OK select the rows which displayed after flter. and delet the selected row.

![filter 2](https://user-images.githubusercontent.com/75326769/141693604-9a156e3b-b62a-4536-bd55-9b53edf2e2f9.png)

#### 🔹 step 3 :  After deleting the rows click on filter icon and removeit.  

![filter3](https://user-images.githubusercontent.com/75326769/141693738-bb92f74f-4223-4d47-bf1d-be624b259540.png)

## 👉 EDA part :-


