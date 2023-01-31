# Capstone
![LOGO](https://user-images.githubusercontent.com/93612651/215375461-6e06ea1d-4e13-425d-b389-e0398460eafe.png)

## Business Overview & Understanding
##   <center> Business Overview </center>



Fire Maul Tools is a firefighter-owned company serving firefighters, tactical teams, and military personnel worldwide by providing innovative tools that were designed for what they do. The company started by producing handmade firefighting tools such as axes and halligan bars, but since then has expanded their product breadth to include items such as tool lube and grip kits. The grip kits are just what they sound like, it is a fiber tape that comes with a lacing ring system that greatly improves grip on the tools. The item has proved to be very popular and the business owner wants to make sure he is getting the most out of the product while keeping his cost down. That is why Fire Maul Tools has tasked me with forecasting the future demand of the grip kits. This way the company can plan its purchasing and inventory levels more effeciently which will lead to lower costs associated with excessive inventory or stockouts. The business owner has stated that since he is a start-up small business his shop is relatively small and does not have a lot of room to inventory the grip kit materials which are shipped to him by the box on pallets. In the past he has been short on supplies when orders come in, but can not afford to take up excess space by over stocking. By following the Data Science methodology and utilizing time-series machine learning techniques, I plan to accomplish solve this problem and help Fire Maul Tools grow as a company so that they can continue to serve First Responders.

**** 
## <center> Data Understanding </center>
 To complete this task, I have been given a dataset with the needed information that will be used with our models. Again, the standard Data Science methodology will be followed:
 -  Obtain the Data
 -  Clean the Data
 -  Exploration
 -  Model
 -  Interpret


A look at the distribution of grip kits sold('Qty)by color:
<img width="954" alt="Screen Shot 2023-01-29 at 8 36 27 PM" src="https://user-images.githubusercontent.com/93612651/215375793-e5a0ca18-6942-4644-8ba2-86412719073b.png">

## <center> Data Prep</center>
After the data was cleaned and we had a grasp of what the data entailed we began to prepare for the modeling process. I was attempting to be able to predict the average number of units sold per week using the quantity column. After an initial run at it, it was decided to remove the outliers and to split the data into a 80/20 train test set. With the dataset being 5 years long it was easy enough to make the most recent year as the test set. After that the dataset had be entered into datimetimeindex, formatted to W-sat, which sets the dates to weeks beginning on Saturday

<img width="889" alt="Screen Shot 2023-01-29 at 8 53 03 PM" src="https://user-images.githubusercontent.com/93612651/215379681-8bedb6d8-5008-49c2-8c22-282909a63482.png">

<img width="921" alt="Screen Shot 2023-01-29 at 9 14 12 PM" src="https://user-images.githubusercontent.com/93612651/215379950-d07c24ca-3945-456f-bbcf-171b1704a2a0.png">

## Models

The method used for the models was based off the SARIMA appendix from Phas3 4.
A range of parameters were set for (p,d,q) and (P,D,Q,s) and a SARIMAX grid search was performed to find the optimal paramters. These parameters were fit to the model and then checked that they did not violate assumptions.
<img width="908" alt="Screen Shot 2023-01-29 at 9 19 20 PM" src="https://user-images.githubusercontent.com/93612651/215380490-03b3da3e-242c-4931-aee9-301f7eadc30e.png">

After the data was fit we used prediction methods such as 'One-step ahead', 'Dynamic' and 'get_forecast' to visualize and print out predicted values and confidence intervals for 'Qty' which is the number of units sold. 

<img width="882" alt="Screen Shot 2023-01-29 at 9 25 02 PM" src="https://user-images.githubusercontent.com/93612651/215381085-728ef2eb-ebe2-4a37-8af0-e0e6e9198646.png">

This method was performed 3 times for the top selling grip kit colors, which were Black, Red, and Blue, these 3 made up over 60% of sales. Therefore there are 3 SARIMA time series models in the notebook. 

## <center> Evaluation </center>
After the models were run and the forecasting methods compared, it was decided that the 'get_forecast' method produced the best results for all 3 models.
Here are visuals that show the predicted average number of units that will be sold each week for the next year, broken down by color.


<img width="826" alt="Screen Shot 2023-01-29 at 9 31 15 PM" src="https://user-images.githubusercontent.com/93612651/215381759-7e3d60f8-41a8-45d2-8554-b62aef523322.png">
The metric used to validate these models was MSE and the get_forecast produced the best results for all 3 models:<br></br>
Black Model MSE: 6.7
<br></br>
Blue Model MSE: 4.95
<br></br>
Red Model MSE : 4.51
<br></br>
A lot of effort went into this and I hope it can be useful for FireMaul Tools!

#### Repo Structure

### ---Jupyter Notebook
### ---Presentation PDF
### ---READMe PDF
### ---Notebook PDF
### ---READMe
### ---Numbers CSV(sales sheet)


Contact Info:
Brian O'Donnell
briodonn1021@gmail.com
