# Airbnb--SQL-
# Airbnb Analysis SQL Intro: 
  When I was studying abroad in London, I wanted to travel to Amsterdam, Netherlands because of the great food, great views, and it is the perfect biking place! (If you don't know already, I love biking!)
  I went to airbnb website to look for a decent place to stay in Amsterdam. When I was scrolling through the page, an idea sparked. I wanted to use SQL to run some analysis to better understand the airbnb in Amsterdam. 
  So I got a dataset that included 500 Amsterdam airbnb hosts information, including price, availability, reviews, url, location, etc. 
  
  In this project, I used SQL to analyze two questions I wanted to explore: 
  # 1. What are the top 15 earners in Amsterdam Airbnb? 
       To answer this question, I need the total revenue for a particular month. However, there is no revenue column. So I decided to use the "price" column and multiply it by the "30-availability_30" as booked rooms
       and arrange them by descending order. 
       
       Some adjustments I made before running analysis: 
       #1. cleaned up the price column by replacing the dollar sign into integer 
       #2. created two new columns: one is "booked_out_room" and one is "proj_rev_month"
       
 # Code I used: 
 Use airbnb;
SELECT 
  l.id, 
  l.listing_url, 
  l.name, 
  (30 - l.availability_30) AS booked_out_room, 
  CONVERT(REPLACE(l.Price, '$', ''), UNSIGNED) AS price_1, 
  CONVERT(REPLACE(l.Price, '$', ''), UNSIGNED) * (30 - l.availability_30) AS proj_rev_month
FROM listings111 AS l
ORDER BY proj_rev_month DESC
LIMIT 15;

I got the following data: 
<img width="832" alt="Screenshot 2023-06-02 at 2 15 43 PM" src="https://github.com/cristinajiang/Airbnb--SQL-/assets/135065815/92cc56e3-daf6-4953-a873-0e17ab8128cf">

As you can see, almost all of the top 15 earners are fully booked, except for one host who still has 4 days available — so I clicked on the listing URL to learn more.

The second question I was interested was: 
# 2. Which airbnb might have the cleanest room? 

Cleaniness of the room is my top priority when travelling. Therefore, I wanted to check which airbnb host received the most review with the word "clean."

# Code I used: 
SELECT 
  l.host_id, 
  l.host_url, 
  l.host_name, 
  COUNT(r.review_id) AS num_clean_reviews
FROM listings111 l
JOIN review r ON r.listing_id = l.id
WHERE r.comments LIKE '%clean%'
GROUP BY l.host_id, l.host_url, l.host_name
ORDER BY num_clean_reviews DESC;

At the end, I was able to check out the link of the top five airbnb hosts that had the best reputation for maintaining "clean" rooms. Out of them, I picked "Daniel" as a host of my preference. 
<img width="476" alt="Screenshot 2023-06-02 at 8 24 55 PM" src="https://github.com/cristinajiang/Airbnb--SQL-/assets/135065815/54a2cb0a-7818-4b16-bb4e-af1866a480c2">



       
  
