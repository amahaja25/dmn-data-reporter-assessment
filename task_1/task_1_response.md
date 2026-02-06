# Task 1
A beat reporter comes to you wanting to scrape [this site](https://www.dallascounty.org/dcpia/search), looking for the grand jury cases for 2023, 2024 and 2025.

**Please write a brief memo that touches on the questions below:**
* What are some of the questions you would ask the reporter before starting the task?
* What are the first three technical checks you would perform to see if scraping is viable?
* What ethical or legal considerations are you considering about scraping?
* If scraping isn't an option, what alternative method would you propose to get this data?
* Explain what are the tools or methods you would employ to scrape the page, you may write pseudo code, but not required.
---

## Questions to ask the reporter:
*  What are you trying to learn from the grand jury cases? Trends over time? Do you want to compare specific offenses?
* Are you interested only in disposition reports or also scheduled cases?
What is the scope of your story? Is this a one-time scrape, or do you want something that flags when new data is updated? 
* When you say 2023 to 2025, are you referring to the date of the offense or the date of the disposition?
* Do you have a particular angle or story idea in mind, or are you just fishing to see if there’s anything interesting in the data?

## Technical checks:
* Before I start scraping, I check for a robots.txt file to see which parts of the website I’d be allowed to scrape. Looking at dallascounty.org/robots.txt I see this: “User-agent: * Allow: /”, which indicates no technical restrictions. However, this doesn’t give me legal permission to scrape the site, so I need to consider terms of use.
* After scrolling to the bottom of the table, I see a link to download a CSV report. This is incredibly helpful, as I don’t need to worry about the HTML table itself and structuring it as a CSV myself. I can instead just download each of the CSVs and combine them into one dataframe for the reporter.
* I would next view the source code to see how the website is structured. Since the form that loads the tables that the reporter wants me to scrape is responsive, I know I’d need to use a library that allows me to emulate a browser, like playwright or selenium, to iterate through each month and year.
* As a bonus, if I hadn’t seen the download link, I’d also look at the network tag to see if there are any APIs that the website pulls data from to see if I can start there and save the trouble of scraping if needed. (However, I don’t see one in this instance)

## Legal or ethical considerations:
* The main ethical or legal worry I would have is whether automated scraping is explicitly banned or restricted. But since the robots.txt file says “Allow: /”, I should be able to scrape this site, though I should still see if I have permission to do so.
* Additionally, since the data contains people’s home addresses, I would not want to publish that personal information to minimize harm and because of privacy concerns. I definitely would not want to republish the raw records found on the site, but rather report findings derived from the data I collect. However, this shouldn’t pose an issue with scraping itself, but rather what the reporter decides to do with the data after they’ve gathered it. This is especially pertinent since the data includes no-bill cases, where the grand jury declined to charge, and I would not want to conflate this with criminality or wrongdoing and amplify harm.
* I would also need to ensure the completeness of the data to ensure it is actually representative of all courts and case types and is not excluding certain categories or months. 

## If scraping isn’t an option, what alternative method would you propose to get this data?
* Since we have download links, the easiest way without scraping would just be to go through each month in these three years and manually click the download links to get all the data instead of automating that process.
* If for whatever reason the download links aren’t working or the county decides to take them away, since the tables are plain HTML, I can copy and paste each table for each month into a spreadsheet and manually create a single spreadsheet that way and retain the format of the tables.
* If all else fails, I would finally consider just emailing the county directly to see if it would be willing to provide the bulk data as a CSV, or filing a records request if all other methods fail. 

## Tools or methods you would employ to scrape the page:
* Since the initial page is responsive and uses JavaScript, I’d use a Python library such as playwright or selenium to emulate a browser to iterate through the months and years.
* After checking the source code, I see that there seems to only be one `<a>` tag on each detail page, which is the link to download, which makes it easy to identify on each page and scrape with BeautifulSoup and/or requests. I’d make sure to employ rate limits so I do not overwhelm the site when scraping.
* I would combine the monthly CSVs together into a single dataframe using pandas, clean the data, check for duplicates and validate against the website to ensure I have all of the data.
