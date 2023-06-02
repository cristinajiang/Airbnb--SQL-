# Airbnb--SQL-
# Airbnb Analysis SQL Intro: 
  When I was studying abroad in London, I wanted to travel to Amersterdan, Netherland because of the great food, great views, and it is the perfect biking place! (If you don't know already, I love biking!)
  I went to airbnb website to look for a decent place to stay in Amersterdan. When I was scrolling through the page, an idea sparked. I wanted to use SQL to run some analysis to better understand the airbnb in Amersterdan. 
  So I got a dataset that included 500 Amersterdan airbnb hosts information, including price, availability, reviews, url, location, etc. 
  
  In this project, I used SQL to analyze two questions I wanted to explore: 
  # 1. What are the top 15 earners in Amersterdan Airbnb? 
       To answer this question, I need the total revenue for a particular month. However, there is no revenue column. So I decided to use the "price" column and multiply it by the "30-availability_30" as booked rooms
       and arrange them by descending order. 
       
       Some adjustments I made before running analysis: 
       #1. cleaned up the price column by replacing the dollar sign into integer 
       #2. created two new columns: one is "booked_out_30" and one is "proj_rev_month"
       
 # Code I used: 
 Use airbnb;
SELECT id, listing_url, name, 30 - availability_30 AS booked_out_30 , 
CAST(REPLACE(Price,'$','') AS UNSIGNED) AS price_1, 
CAST(REPLACE(Price,'$','') AS UNSIGNED)*(30 - availability_30) AS proj_rev_month
FROM listings111 ORDER BY proj_rev_month DESC LIMIT 15; 

and I got the following data: 
<img width="832" alt="Screenshot 2023-06-02 at 2 15 43 PM" src="https://github.com/cristinajiang/Airbnb--SQL-/assets/135065815/92cc56e3-daf6-4953-a873-0e17ab8128cf">

as you can see, almost all 15 top earners are booked out except one that still had 4 days availability. So I clicked on its url and checked it out. 


       
       
  
