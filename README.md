
# SQL PROJECT
# Analysis of Car Sales 


## Introduction

The project aims to analyze a dataset containing information about car sales. This dataset encompasses various attributes such as the car's name, year of manufacture, selling price, mileage, fuel type, transmission type, owner details, and more. The analysis seeks to extract meaningful insights to understand market trends, pricing dynamics, and consumer preferences within the automotive industry.

### Dataset Description

- The dataset consists of a list of vehicles along with their specifications and sales details.
- Key attributes include the name of the car, year of manufacture, selling price, mileage, fuel type, transmission type, owner details, engine specifications, torque, and seating capacity.
- The dataset covers a range of car models, fuel types (petrol, diesel, electric), transmission types (manual, automatic), and owner statuses.

### Objectives
- To understand the distribution of car sales across different years, fuel types, and transmission types.
- To analyze the relationship between selling price and various attributes such as mileage, engine specifications, and owner details.
- To identify trends in the market, including the popularity of certain car models, fuel types, and transmission types.
- To explore factors influencing the selling price of cars and identify potential predictors.
- To provide insights that can be utilized for strategic decision-making by stakeholders in the automotive industry, including manufacturers, dealerships, and consumers.




### Steps followed 

- Step 1 : Load data into MySql, dataset is a csv file.
- Step 2 : Analysis 


### 1.	READ THE CAR DATA

    SELECT * FROM CAR_DATA;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/1b65c659-e166-439c-8119-fa59315eaf67)


### 2.	TOTAL CARS 

    SELECT COUNT(*) FROM CAR_DATA;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/5fea39b0-e3c1-43dc-a2e1-5d353fdaa0ab)


### 3.	HOW MANY CARS WILL BE AVAILABE IN 2014 

    SELECT COUNT(*) FROM CAR_DATA 
    WHERE YEAR = "2014";

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/32413cd9-c167-4586-80e5-2b7045f7d3a1)

### 4.	HOW MANY CARS IS AVAILABLE IN 2014,2015,2016?

     SELECT YEAR, COUNT(*)AS TOTAL_CARS 
     FROM CAR_DATA 
     WHERE YEAR IN (2014,2015,2016) 
     GROUP BY YEAR;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/9348c555-0324-4713-9d33-bf20d6175270)

### 5. CLIENT ASKED TOTAL OF ALL CARS BY YEAR I DONT WANT ALL DETAILS 

    SELECT YEAR, COUNT(*) AS TOTAL_CARS
    FROM CAR_DATA 
    GROUP BY YEAR;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/ee941872-3bb3-4c54-b29e-76b38564c766)

### 6. CLIENT ASKED CAR DEALER AGENT HOW MANY DIESEL CARS WILL BE THERE IN 2014 

     SELECT COUNT(*) AS TOTAL_CARS 
     FROM CAR_DATA 
     WHERE YEAR = 2014 AND FUEL_TYPE = "DIESEL";

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/d4f4eb4b-ea00-4884-8d6a-de246079a69c)

### 7. CLIENT ASKED CAR DEALER AGENT HOW MANY DIESEL CARS WILL BE THERE IN 2020 

     SELECT COUNT(*)AS TOTAL_CARS 
     FROM CAR_DATA 
     WHERE  YEAR = 2014 AND FUEL_TYPE = "PETROL";

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/648109db-e4a8-418b-a171-bcfddc9cefdf)


### 8. MANAGER ASKED TOTAL CARS ALL YEAR FUEL TYPE (DIESEL,PETROL,CNG)

        SELECT YEAR,FUEL_TYPE, COUNT(*) AS TOTAL_CARS 
        FROM CAR_DATA 
        WHERE FUEL_TYPE IN ("DIESEL","PETROL","CNG")
        GROUP BY YEAR,FUEL_TYPE;
        
![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/8b6e3272-aa4c-4deb-afb3-33d015686d7e)

### 9. MANAGER SAID THERE WHERE MORE THAN 50 CARS IN A GIVEN YEAR, WHICH YEAR HAD MORE THAN 50 CARS

        SELECT YEAR, COUNT(*) 
        FROM CAR_DATA 
        GROUP BY YEAR 
        HAVING COUNT(*) > 50;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/80b1125b-d915-458a-9347-4d87410a6beb)

### 10. MANAGER SAID THERE WHERE LESS THAN 100 CARS IN A GIVEN YEAR, WHICH YEAR HAD LESS THAN 50 CARS 

        SELECT YEAR, COUNT(*) 
        FROM CAR_DATA 
        GROUP BY YEAR 
        HAVING COUNT(*) < 50;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/ddfc1b11-13d7-424c-a334-9b15d3b29fb6)

### 11. MANAGER SAID TO EMPLOYEE ALL CARS COUNT DETAILS BETWEEN 2015 AND 2023,

        SELECT COUNT(*) 
        FROM CAR_DATA 
        WHERE YEAR BETWEEN 2015 AND 2023;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/1c9d81a6-086b-48d1-b8c5-6435a9b86607)

### 12. THE MANAGER SAID TO THE EMPLOYEE ALL CARS DETAILS BETWEEN 2015 AND 2023 NEED COMPLETE LIST

        SELECT * FROM CAR_DATA 
        WHERE YEAR BETWEEN 2015 AND 2023;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/779d985b-bec3-4e0b-8f1c-b75dd6954bd2)

### 13. FIND THE AVERAGE SELLING PRICE AND TOTAL MILEAGE DRIVEN FOR EACH COMBINATION OF FUEL TYPE AND TRANSMISSION

        SELECT FUEL_TYPE, TRANSMISSION, 
        AVG(SELLING_PRICE) AS AVG_SELLING_PRICE, 
        SUM(KMS_DRIVEN) AS TOTAL_MILEAGE
        FROM CAR_DATA
        GROUP BY FUEL_TYPE, TRANSMISSION;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/47ca8b0f-b574-4baa-bc88-550e91229876)

### 14. IDENTIFY THE TOP 5 CARS WITH THE HIGHEST SELLING PRICE

        SELECT CAR_NAME, YEAR, SELLING_PRICE 
        FROM CAR_DATA 
        ORDER BY SELLING_PRICE 
        DESC LIMIT 5;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/7d550ecc-bee2-4067-82b3-eeaae5152ab5)

### 15. CALCULATE THE TOTAL NUMBER OF CARS SOLD AND THE AVERAGE SELLING PRICE FOR EACH YEAR:

        SELECT YEAR, COUNT(*) AS NUM_VEHICLES_SOLD, 
        AVG(SELLING_PRICE) AS AVG_SELLING_PRICE 
        FROM CAR_DATA GROUP BY YEAR;

![image](https://github.com/arvindbadagi/Car-Data-Analysis/assets/160807783/260ef411-a5d0-486f-a7cf-619baf997d37)


