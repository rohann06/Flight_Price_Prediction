# Flight_Price_Prediction

#### ➡️ This supervised machine learning model predict the price of the Flight ticket using some parameters

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

#### 🔸 step 1 : In EDA part, first of all we find some odd columns which neet to be fixed, colimns like "Date_of_journey", "dep_time", "Arrival_time".


![EDA 1](https://user-images.githubusercontent.com/75326769/141733110-ba83c430-f546-4c64-bb4b-1930856e40b8.png)

#### 🔸 step 2 :  For the "Date_of_jorney" I've create one function named "date" and and using (pd.to_datetime) Picked the journey bay and journey month from it and drop the Date_of_jorney column.

```py
def date(data):
    data['Journey_day'] = pd.to_datetime(data['Date_of_Journey'], format="%d/%m/%Y").dt.day
    data['Journey_month'] = pd.to_datetime(data['Date_of_Journey'], format="%d/%m/%Y").dt.month
    data.drop(["Date_of_Journey"], axis = 1, inplace = True)
```

#### 🔸 step 3 : There are two columns with the same formats name "Dep_Time", "Arrival_Time". to solve this I've Picked the Dep_hours and Dep_min and, Arrival_hours and Arrival_min using same (pd.to_datetime) adn droped bothe the columns.

#### For Dep_Time :

```py
def dep_time(data):
    data["Dep_hour"] = pd.to_datetime(data["Dep_Time"]).dt.hour
    data["Dep_min"] = pd.to_datetime(data["Dep_Time"]).dt.minute
    data.drop(["Dep_Time"], axis = 1, inplace = True)
```

#### Fro Arrival_Time :

```py
def Arrival_time(data):
    data["Arrival_hour"] = pd.to_datetime(data["Arrival_Time"]).dt.hour
    data["Arrival_min"] = pd.to_datetime(data["Arrival_Time"]).dt.minute
    data.drop(["Arrival_Time"], axis = 1, inplace = True)
```


#### 🔸 step 4 : Picking the hours and minutes from the "Duration" coloumn

```py
def duration(data):
    duration = list(data["Duration"])

    for i in range(len(duration)):
        if len(duration[i].split()) != 2:    # Check if duration contains only hour or mins
            if "h" in duration[i]:
                duration[i] = duration[i].strip() + " 0m"   # Adds 0 minute
            else:
                duration[i] = "0h " + duration[i]           # Adds 0 hour

    duration_hours = []
    duration_mins = []
    for i in range(len(duration)):
        duration_hours.append(int(duration[i].split(sep = "h")[0]))    # Extract hours from duration
        duration_mins.append(int(duration[i].split(sep = "m")[0].split()[-1]))   # Extracts only minutes from duration
    data["Duration_hours"] = duration_hours
    data["Duration_mins"] = duration_mins 
    
    data.drop(["Duration"], axis = 1, inplace = True)
```


## 👉 Select the Algorithm :-
![Screenshot 2021-11-15 135539](https://user-images.githubusercontent.com/75326769/141747405-ccafe4e7-071f-4192-a68a-ff4a1d04cdfc.png)

#### -> As we see in this comparision table the "DecisionTreeRegressor" performing very well on the dataset
![algo](https://user-images.githubusercontent.com/75326769/141749087-9cd07037-b899-4d49-9f61-418aef964bad.png)

 


