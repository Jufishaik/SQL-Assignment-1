# SQL-Assignment-1
select * from fifa_data;

# How many Players are there in the dataset?
select count(*) as cnt from fifa_data;

# How many Nationalities does this player belongs to?
select distinct nationality as nation from fifa_data;
select count(distinct nationality) as tot_nationalities from fifa_data;

# Which Nationality has Highest no.of players,what are the top 3 nationalities by # of players?
select nationality, count(*) as player_count
from fifa_data
group by nationality
order by player_count desc
limit 3;

# what is the total wage given to all the players?what is average and standard deviation?
select sum(wage) as total_wage,
avg(wage) as total_avg,
stddev(wage) as std_wage
from fifa_data;

select count(wage) as total_wage,
avg(wage) as avg_wage,
stddev(wage) as std_wage
from fifa_data;

# Which player has highest wage?who has the lowest?
select name, wage
from fifa_data
order by wage desc limit 1;

# Lowest Wage
select name, wage
from fifa_data
order by wage asc limit 1;


# The player having the best overall rating? Worst overall rating?
select name,overall 
from fifa_data
order by Overall desc limit 1;

# worst overall rating
select name,overall 
from fifa_data
order by Overall asc limit 1;


# Club having the highest total of overall rating? Highest average of overall rating?
select overall as total_overall,
avg(overall) as avg_overall
from fifa_data
order by overall limit 1;

select club, sum(overall) as total_rating
from fifa_data
group by club
order by total_rating desc limit 1;


select club, avg(overall) as avg_rating
from fifa_data
group by club
order by avg_rating desc limit 1;

# what are the top 5 clubs based on the average rating of their players? 
select club as avg_rating
from fifa_data 
order by overall desc limit 5;

select club, avg(overall) as avg_rating
from fifa_data
group by club
order by avg_rating desc limit 5;


# What is the distribution of players whose preferred foot is left vs right?
select preferred_foot, count(*) as player_count
from fifa_data
group by preferred_foot;


# Which jersey number is the luckiest?
select jersey_number, count(*) as player_count
from fifa_data
group by jersey_number
order by player_count desc
limit 1;

# What is the frequency distribution of nationalities among players whose club name starts with M?
select nationality, count(*) as player_count
from fifa_data
where club like 'M%'
group by nationality
order by player_count desc;

# How many players have joined their respective clubs in the date range 20 May 2018 to 10 April 2019(both inclusive)?
select count(*) as total_players
from fifa_data
where join_date between '2018-05-20' and '2019-04-10';

# How many players have joined their respective clubs date wise?
select join_date, count(*) as player_count
from players
group by join_date
order by join_date;

# How many players have joined their respective clubs yearly?
select year(join_date) as join_year, 
count(*) as player_count
from players
group by year(join_date)
order by join_year;


