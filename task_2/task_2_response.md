# Task 2
A beat reporter provides you with a list of Dallas city council members and the campaign finance data that’s [publicly available here](https://www.dallasopendata.com/Services/Campaign-Finance/ndxz-gccx/about_data). The reporter does not have a clear pitch or idea, and is essentially on a “fishing expedition.”

**City council members:**
Eric Johnson, Chad West, Jesse Moreno, Zarin Gracey, Maxie Johnson, Jaime Resendez, Laura Cadena, Adam Bazaldua, Lorie Blair, Paula Blackmon, Kathy Stewart, William Roth or Bill Roth, Cara Mendelsohn, Gay Donnell Willis, Paul Ridley.

**Please prepare a memo that touches on:**
* What are the first steps you would take to assess the dataset’s strength and weaknesses?
* What are the strengths and weaknesses of this dataset?
* What are some possible angles/potential data stories you would pitch based on your initial assessment?

---
## Steps taken to assess strength and weaknesses:
* To assess the dataset’s strengths and weaknesses, I’d look at the structure of the dataset and what each column represents (amount, record type, election date, contributor or vendor details, etc.).
* I would look at the years the data spans, and check if there are any gaps in coverage.
* I’d count to see the number of total records and look for any duplicate rows or NAs.
* I would check to see if the contributions and expenditures are line-item contributions or if they are aggregated totals.
* I’d cross-check the list of council members to the candidate names in the dataset to see if anyone is missing or if people go by different names. 
    * For example, Jesse Moreno does not show up, but that’s because he’s listed as Jesus Moreno, his birth name.
* I’d look for outliers or any patterns in the data that raise red flags.

## Strengths and weaknesses:
### Strengths 	
* The dataset is updated periodically, which is useful in that we can get the most updated information frequently. But this also means that manually exporting the data is likely inefficient, so we’d likely have to set up some form of automated pipeline to grab the updated dataset at a certain interval to ensure we’re not working with outdated information.  
* The dataset includes both contributions and expenditures with detailed amounts.
* The dataset links to the original PDF filings, which allow for verification of the reports.
* The data includes addresses, which allows for geocoding to map donor or vendor locations. 
### Weaknesses:
* Some of the transactions seem to be linked to elections almost five years prior, with transaction dates in 2025 but election dates in 2019. Since campaign finance accounts should close after election cycles, this stood out to me as a major red flag. This could either be late filings, or could be an issue with the data quality. I’d need to do some additional reporting to better out why this occurred or if there's a story there.
* A significant proportion of the Candidate/Committee records had $0 amounts, which also seemed strange, but most of these rows were referring to the links to reports rather than contributions or expenditures. The data is duplicated, with multiple rows for the expenditure and the report itself. 
* The vendor names are not clean. For example, the same vendor shows up as both “Catalyst Advisors Group, LLC” and “CATALYST ADVISORS GROUP LLC”. 
* Though the data has addresses, some are already geocoded while others are not — this means I’d need to geocode all of the addresses myself for consistency.
* The data also does not include expenditure type, which is in the original PDF filings. I’m interested in the distinction between food and beverage expense versus contract labor versus travel, but I can’t explore this without getting that information from the PDFs myself.

## Angles/potential data stories
* I’m interested in seeing which city council districts have the most expensive races, and which candidates receive the most in contributions. Since I do not have data on transactions before 2024, my scope is a bit limited, but this could provide some insight into how competitive some races are, and if there are significant variations in fundraising across the city geographically.
* Additionally, I’m interested in seeing which city council candidates had the largest deficits between the money they earned versus the money they spent.
* I’m curious to further examine money flowing from out of state to see whether national interests play a role in local races, and if there are some candidates that rely more heavily on non-local donors than others.
* I’m curious if the same firms or vendors are paid across multiple candidates’ campaigns to see if there are groups of service providers that contract with multiple candidates.
* With clean geocoded addresses, I’d be interested in seeing the geographic pattern of contributions. I’d combine this with Census data to see if donations cluster in particular neighborhoods or if there is any tie to demographics.
