# Task 3
You have just finished a complex analysis for a front-page story. You are going on vacation the week the story runs. An editor (not the data editor) needs to double-check your numbers, and your graphics colleagues may need to build charts or update graphics.

**Please detail for us:**
* How do you structure your files/folders so a non-technical colleague can navigate them?
* What specific documentation do you provide?

**Bonus:** Provide a generic example of a README file you would include in a repository.

--- 
<br>

I structure my files and folders with clear names so the editor can intuitively get a sense where things are located even without technical knowledge. For example, raw_data/ contains original datasets as I received them. After cleaning the data before analysis, I also export a clean sheet. This ensures the editor can fact-check my work themselves in a spreadsheet and trace my steps without using any code. Similarly, when I’m analyzing data specifically for graphics, I export the data I need for that graphic as its own CSV. This will save my editors and colleagues from the trouble of changing column names, transposing data, removing unnecessary columns or any other friction that could come up when updating graphics, but still allows them to fact-check me. These CSVs are in my output folder.

In the README, I clearly outline what each of the folders are and what they contain. I also provide a data dictionary, so my editor knows what each column means, its unit if relevant, and what the dataset contains. I also provide the source of the data, as well as any limitations to the analysis. I include a methodology section with general steps I took to analyze the data with non-technical language so it can be reproduced. For more specific steps, I’d typically rely on my comments in each cell of my Python notebook. 

Below is an example of how I’d structure my repo: <br>

repo-name
* README.md
* requirements.txt
* .gitignore
* raw_data/
    * 2025
        * csv1-2025.csv
        * csv2-2025.csv
    * 2024
        * csv1-2024.csv
* clean_data/
    * cleaned_data.csv
* output/
    * formatted_data_bar_chart.csv
    * formatted_data_map.csv
* analysis/
    * analysis.ipynb
    * analysis_helper_functions.py
    * clean_data.py
