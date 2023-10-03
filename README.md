DATA PREPARATION

The DataFrame has 12684 rows and 26 columns with both int64 and object formatted data
columns. The following columns contain missing values. 

     • car	 		     12,576
     • Bar				107
     • CoffeeHouse			217
     • CarryAway			151
     • RestaurantLessThan20		130
     • Restaurant20To50			189
	  
The dataset was prepared for subsequent analysis by:
	
 • Removing 74 duplicate rows.
 • Removing the ‘car’ column because of the sparse nature of the data
 • Removing the ‘toCoupon_GEQ5min’ column because all its values were equal to 1, which
   is not a believable situation, indicating that the data was not reliable. 
 • Removing the corresponding rows for the remaining missing values as indicated above
	 
The resulting dataset contained 12,007 rows and 24 columns which was further checked
and modified as follows:
	
 • The ‘passanger’ column was renamed to ‘passenger’.
 • The ‘direction_same’ and the ‘direction_opp’ columns were checked for consistency
   since they contain the same information with opposite polarity. In other words, 
   direction_same = 1 should be equivalent to direction_opp = 0, and direction_same = 0
   should be equivalent to direction_opp = 1. No discrepancies were found, but the 
   corresponding rows for any discrepancies would have been removed if they had existed. 
		
Heat maps of the numeric variables show there are no significant correlations between the
variables, indicating they serve as independent measures of drivers' likelihood of
accepting coupons.

KEY FINDINGS

1) Overall
     a.	Drivers who visit coffeehouses more frequently tend to have higher coupon acceptance
        rates.
     b.	Drivers were more likely to accept coupons if someone else was in the car with friends
        and partners having nearly equal impacts and exceeding acceptance rates with kids.
     c.	Younger drivers were more likely to accept coupons than older drivers. This is 
        particularly true for the ‘Never’ category, where all the age categories above the early
   	twenties had much lower acceptance rates.
     d.	Drivers in the $62.5k – $87.5k were the least likely to accept coupons.
     e.	There was no significant difference in acceptance rates by gender.
     f.	Drivers with no college education were more likely to accept coupons.
     g.	Drivers were more likely to accept coupons on rainy and warm days with temperatures
        around 80 degrees, and least likely to accept coupons during snow events.
     h.	Drivers were more likely to accept coupons when they had no urgent destination, or
        they were heading to work. Heading home resulted in the lowest acceptance rates.
     i.	Shorter coupon expirations always led to lower acceptance rates.
     j.	Drivers were slightly more likely to accept coupons if they did not have to switch
        directions to reach the coffee house.

3) I also looked at the acceptance rate of CoffeeHouse Coupons. Mean Coupon Acceptance
   Rates for Each 'CoffeeHouse' Category are as follows:
	
     • 1 to 3 times		64.7%
     • 4 to 8 times		68.2%
     • Less than 1 time		48.0%
     • More than 8 times	65.8%
     • Never 			17.5%

   The ‘Never’ and ‘Less than 1 Time’ categories show means that are significantly
   different than the other categories, suggesting the factors that determine acceptance
   rates for them are significantly different than the others. Therefore, I segmented
   the data into three classes of drivers for the analysis: ‘Never’, ‘Less than 1 Time’, and
   ‘Other’. The ‘Other’ category merges the remaining three categories with nearly
   equal acceptance rates. The subsequent analysis was based on these three categories
   and was implemented to make recommendations for targeting drivers with the desired
   characteristics in each category. The mean acceptance rates for these three
   categories are:
	
     • Never						17.5%
     • Less than 1 time					48.0%
     • Other						65.9%

4) By far, the most important factor driving higher acceptance rates is a driver’s 
   occupation. By targeting the top three occupations in each category, acceptance
   rates exceed the baseline mean for each category by ~15%:
	
   ‘Never’ Category (Mean: 17.5%)
     • Architecture & Engineering			73.3%
     • Installation Maintenance & Repair		42.9%
     • Life Physical Social Science			30.0%

   ‘Less than 1 time’ Category (Mean: 48.0%)
     • Building & Grounds Cleaning Services		72.7%
     • Students						65.4%
     • Healthcare Support				61.9%

   ‘Other’ Category (Mean: 65.9%)
     • Healthcare Practitioners & Techs			90.0%
     • Personal Care & Services				88.9%
     • Construction and extraction			87.5%

5) The column/category combinations that have the highest acceptance rates in each category are provided in the following tables from highest to lowest. While the tables are dominated by specific occupations, we can see that other categories not associated with specific occupations are significant as well. Ech table presents the top column/category combinations that have the highest acceptance rates for each class of driver:

   Results for 'Never' category
   Overall Mean for 'Never' category: 17.5%
	
     Column		Category 			Acceptance Rate
     Occupation		Architecture & Engineeri	73.3%
     education		Some High School		50.0%
     occupation		Installation Maintenance	42.9%
     weather		Rainy				31.5%
     age		41				31.0%
     occupation		Student				30.6%
     occupation		Life Physical Social Sci	30.0%
     age		46				30.0%
     income		$50000 - $62499			29.4%
     education		High School Graduate		29.3%
     occupation		Construction & Extractio	26.7%
     income		$37500 - $49999			26.0%
     age		21				25.8%
     occupation		Retired				25.4%
     passenger		Friend(s)			25.0%
     occupation		Protective Service		25.0%
     maritalStatus	Widowed				23.8%
     income		$12500 - $24999			23.5%
     passenger		Partner				23.1%
     occupation		Production Occupations		23.1%

Results for 'Less than 1 time' category
Overall Mean for 'Less than 1 time' category: 48.0%

     Column		Category			Acceptance Rate
     occupation		Building & Grounds Clean	72.7%
     age		36				66.7%
     maritalStatus	Divorced			66.7%
     occupation		Student				65.4%
     occupation		Healthcare Support		61.9%
     occupation		Transportation & Materia	61.9%
     education		Associates degree		60.5%
     income		$50000 - $62499			59.8%
     destination	No Urgent Place			58.0%
     passenger		Friend(s)			58.0%
     weather		Rainy				56.9%
     income		Less than $12500		56.4%
     occupation		Healthcare Practitioners	56.3%
     gender		Male				56.0%
     expiration		1d				55.8%
     occupation		Computer & Mathematical		54.6%
     maritalStatus	Widowed				53.8%
     education		High School Graduate		53.8%
     income		$100000 or More			53.8%
     passenger		Partner				53.3%

Results for 'Everyone Else' category
Overall Mean for 'Everyone Else' category: 49.6%

     Column		Category			Acceptance Rate
     Occupation		Healthcare Practitioners	76.1%
     Occupation		Building & Grounds Clean	72.7%
     Occupation		Transportation & Materia	61.8%
     Occupation		Healthcare Support		61.5%
     Occupation		Student				61.5%
     Education		Some High School		60.7%
     Passenger		Friend(s)			59.7%
     Expiration		1d				58.0%
     Destination	No Urgent Place			57.7%
     Occupation		Installation Maintenance	56.8%
     Passenger		Partner				56.6%
     Occupation		Architecture & Engineeri	55.6%
     Income		$12500 - $24999			55.2%
     Income		$37500 - $49999			54.7%
     Occupation		Farming Fishing & Forest	54.5%
     toCoupon_GEQ15min	0				54.4%
     education		High School Graduate		54.0%
     income		Less than $12500		54.0%
     occupation		Unemployed			53.7%
     income		$87500 - $99999			53.6%

5) Next steps would include selecting the columns/cetegory combinations with acceptance rates greater than the nominal acceptance rates for each of the three classes of drivers. Screening drivers always results in subsets of drivers, so attention must also be given to the sizes of the screened datasets. In other words, screening will often result in significantly higher acceptance rates, but the size of the screened drivers is so small that very few coupons get issueed.
