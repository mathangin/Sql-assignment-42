# Sql-assignment-42
From google big query, the census_bureau_international data of international public data of world development index has been used for running SQL commands. 3 tables have been used namely: age_specific_fertility_rates, birth_death_growth_rates, mortality_life_expectancy. 
1.	From the age_specific_fertility_rates table, which are the 20 countries with high gross reproduction rate?
select country_name, year,fertility_rate_20_24, fertility_rate_25_29, fertility_rate_30_34, total_fertility_rate, gross_reproduction_rate, sex_ratio_at_birth from  `bigquery-public-data.census_bureau_international.age_specific_fertility_rates` where year=2019
order by gross_reproduction_rate desc limit 20
country_name	year	fertility_rate_20_24	fertility_rate_25_29	fertility_rate_30_34	total_fertility_rate	gross_reproduction_rate	sex_ratio_at_birth
Niger	2019	261.4	271.4	238.6	6.2152	3.0617	1.03
Angola	2019	252.6	271.7	239.7	6.0282	2.9696	1.03
Burundi	2019	257.6	282.2	250.4	5.882	2.8975	1.03
Mali	2019	253.6	256.1	220.7	5.82	2.867	1.03
Chad	2019	259.3	269.5	232	5.79	2.8382	1.04
Somalia	2019	240.3	268.1	232.1	5.606	2.7616	1.03
South Sudan	2019	250.1	241.3	229.8	5.65	2.7561	1.05
Zambia	2019	255	254.7	217.7	5.536	2.7271	1.03
Uganda	2019	251.1	259.5	222.6	5.53	2.7241	1.03
Malawi	2019	254.1	239.6	193.1	5.3714	2.6657	1.015
Mozambique	2019	199.7	214.1	191.4	4.958	2.4581	1.017
Liberia	2019	213.3	212.9	189.6	4.952	2.4394	1.03
Guinea	2019	200.8	219.5	193.6	4.95	2.4384	1.03
Afghanistan	2019	196.4	245.1	205.1	4.92	2.4	1.05
Ethiopia	2019	199.1	231.1	196.5	4.83	2.3793	1.03
Guinea-Bissau	2019	186.7	216.7	189.9	4.782	2.3557	1.03
Sudan	2019	191.3	243.6	211.8	4.7875	2.3354	1.05
Nigeria	2019	200	242.9	202.4	4.786	2.3233	1.06
Sierra Leone	2019	200.5	203.3	174.5	4.6559	2.2935	1.03
Tanzania	2019	218.6	221.5	183.7	4.65	2.2906	1.03

2.	From the age_specific_fertility_rates table, which are the 5 countries with the least total fertility rate in the year 2019?
select country_name, year,fertility_rate_20_24, fertility_rate_25_29, fertility_rate_30_34, total_fertility_rate, gross_reproduction_rate, sex_ratio_at_birth from  `bigquery-public-data.census_bureau_international.age_specific_fertility_rates` where year=2019
order by total_fertility_rate asc limit 5
country_name	year	fertility_rate_20_24	fertility_rate_25_29	fertility_rate_30_34	total_fertility_rate	gross_reproduction_rate	sex_ratio_at_birth
Singapore	2019	12	41.4	69.2	0.854	0.412	1.0729
Macau	2019	32.8	56.7	63.9	0.9549	0.4658	1.0498
Taiwan	2019	29.2	69.9	82.6	1.1368	0.5513	1.0619
Hong Kong	2019	26.6	63.6	86.6	1.2042	0.5814	1.0711
Puerto Rico	2019	80.3	62.5	40.1	1.2221	0.5936	1.0589

3.	From the age_specific_fertility_rates table, which are the 5 countries with sex ratio at birth less than equal to one in the year 2019?
select country_name, year,fertility_rate_20_24, fertility_rate_25_29, fertility_rate_30_34, total_fertility_rate, gross_reproduction_rate, sex_ratio_at_birth from  `bigquery-public-data.census_bureau_international.age_specific_fertility_rates` where year=2019 and sex_ratio_at_birth <= 1
country_name	year	fertility_rate_20_24	fertility_rate_25_29	fertility_rate_30_34	total_fertility_rate	gross_reproduction_rate	sex_ratio_at_birth
Kazakhstan	2019	113.3	136.5	102.5	2.19	1.1307	0.9368
Nauru	2019	130.6	164.5	125.8	2.72	1.4836	0.8333
United States	2019	84.17	106.32	92.71	1.869635599	-9	-9

4.	From the birth_death_growth_rates table, which are the 20 countries with  crude birth rate or crude death rate equal to 5 ?
select country_name, year, crude_birth_rate, crude_death_rate , growth_rate from `bigquery-public-data.census_bureau_international.birth_death_growth_rates` where crude_birth_rate =5 or crude_death_rate = 5 limit 20
country_name	year	crude_birth_rate	crude_death_rate	growth_rate
Egypt	2047	18.31	5	1.309
Brunei	2032	14.27	5	1.119
Ecuador	2006	22.13	5	1.551
Ecuador	2007	21.67	5	1.556
Ecuador	2010	20.32	5	1.466
Ecuador	2011	19.96	5	1.443
Malaysia	2003	24.03	5	2.689
Malaysia	2014	20.06	5	1.473
Maldives	2032	11.99	5	0.699
Hong Kong	1991	11.87	5	1.134
Venezuela	2007	22.03	5	1.544
Timor-Leste	2034	23.71	5	1.513
Timor-Leste	2042	20.47	5	1.21
Guinea-Bissau	2042	31.3	5	2.41
American Samoa	2013	21.5	5	-1.026
Cayman Islands	2010	12.29	5	2.338
Marshall Islands	2003	34.19	5	2.301
Virgin Islands, British	1992	17.37	5	3.997
Turks and Caicos Islands	1992	31.25	5	5.313
Angola	2042	34.12	5	2.913

5.	From the mortality_life_expectancy table, what is the average of infant mortality for the year 2019?
select avg (infant_mortality) from  `bigquery-public-data.census_bureau_international.mortality_life_expectancy` where year =2019
f0_
20.58666667

6.	From the mortality_life_expectancy table, what is the minimum value of life expectancy for the year 2019?
select min (life_expectancy) from  `bigquery-public-data.census_bureau_international.mortality_life_expectancy` where year =2019
f0_
52

7.	From the mortality_life_expectancy table, what is the maximum value of life expectancy of females for the year 2019?
select max (life_expectancy_female) from  `bigquery-public-data.census_bureau_international.mortality_life_expectancy` where year =2019
f0_
93.32

8.	For the year 2019, show the inner join for the first 20 values of crude birth rate from the birth_death_growth_rates table and life expectancy from the mortality_life_expectancy table
select  `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.crude_birth_rate, `bigquery-public-data.census_bureau_international.mortality_life_expectancy`.life_expectancy, `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.year from `bigquery-public-data.census_bureau_international.birth_death_growth_rates` inner join `bigquery-public-data.census_bureau_international.mortality_life_expectancy` on `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.country_name= `bigquery-public-data.census_bureau_international.mortality_life_expectancy`.country_name
where `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.year = 2019 limit 20
crude_birth_rate	life_expectancy	 year
12.21	72.86	2019
12.21	72.88	2019
12.21	72.9	2019
12.21	72.91	2019
12.21	72.92	2019
12.21	72.94	2019
12.21	72.95	2019
12.21	72.95	2019
12.21	72.96	2019
12.21	72.97	2019
12.21	72.97	2019
12.21	72.97	2019
12.21	72.84	2019
12.21	72.87	2019
12.21	72.82	2019
12.21	72.88	2019
12.21	72.75	2019
12.21	72.9	2019
12.21	72.89	2019
12.21	72.88	2019

9.	For the year 2019, show the full outer join for the first 20 values of crude death rate from the birth_death_growth_rates table and life expectancy female from the mortality_life_expectancy table

select `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.crude_death_rate,`bigquery-public-data.census_bureau_international.mortality_life_expectancy`.life_expectancy_female  from `bigquery-public-data.census_bureau_international.birth_death_growth_rates` full outer join  `bigquery-public-data.census_bureau_international.mortality_life_expectancy` on `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.country_name= `bigquery-public-data.census_bureau_international.mortality_life_expectancy`.country_name where `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.year = 2019 limit 20
crude_death_rate	life_expectancy_female
10.24	49.59
10.24	49.79
10.24	49.98
10.24	50.18
10.24	50.37
10.24	50.56
10.24	50.75
10.24	50.93
10.24	51.44
10.24	51.94
10.24	52.44
10.24	52.93
10.24	53.41
10.24	53.89
10.24	54.36
10.24	54.83
10.24	55.29
10.24	55.74
10.24	56.19
10.24	56.63

10.	For the year 2019, show the right join for the first 20 values of growth rate from the birth_death_growth_rates table and life expectancy from the mortality_life_expectancy table 

select `bigquery-public-data.census_bureau_international.birth_death_growth_rates`. growth_rate,`bigquery-public-data.census_bureau_international.mortality_life_expectancy`.life_expectancy  from `bigquery-public-data.census_bureau_international.birth_death_growth_rates` right join  `bigquery-public-data.census_bureau_international.mortality_life_expectancy` on `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.country_name = `bigquery-public-data.census_bureau_international.mortality_life_expectancy`.country_name where `bigquery-public-data.census_bureau_international.birth_death_growth_rates`.year = 2019
order by `bigquery-public-data.census_bureau_international.birth_death_growth_rates`. growth_rate limit 20 
growth_rate	life_expectancy
-5.384	69.26
-5.384	67.3
-5.384	68.54
-5.384	68.35
-5.384	69.09
-5.384	69.75
-5.384	69.59
-5.384	66.84
-5.384	67.74
-5.384	67.52
-5.384	70.2
-5.384	68.73
-5.384	67.95
-5.384	67.07
-5.384	66.59
-5.384	70.05
-5.384	69.9
-5.384	69.43
-5.384	68.15
-5.384	68.91

