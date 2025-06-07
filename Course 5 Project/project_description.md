## Project Overview
This project has two parts that demonstrate the importance and value of data visualization techniques in the data analysis process.
* In Part I, __Exploratory__ data visualization, you will use Python visualization libraries to systematically explore a selected dataset, starting from plots of single variables and building up to plots of multiple variables.
* In Part II, __Explanatory__ data visualization, you will produce a short presentation that illustrates interesting properties, trends, and relationships that you discovered in your selected dataset. The primary method of conveying your findings will be through transforming your exploratory visualizations from the first part into polished, explanatory visualizations.


## Instructions - Part I
### Part 1 - Exploratory Data Analysis
In this first part, you will conduct an exploratory data analysis on a dataset of your choice. Use Python data science and data visualization libraries to explore the dataset’s variables and understand the data’s structure, oddities, patterns, and relationships.

The analysis in this part should be structured, going from simple univariate relationships to multivariate relationships, but it does not need to be clean or perfect. There is no single answer that needs to come out of a given dataset. This part of the project is your opportunity to ask questions about the data and make your discoveries. It’s essential to keep in mind that sometimes exploration can lead to dead ends and that it can take multiple steps to dig down to what you’re genuinely looking for. Be patient with your steps, document your work carefully, and be thorough in the perspective that you choose to take with your dataset.

Here are the steps you need to follow:
#### 1.1. Dataset
[Ford GoBike System Data](https://video.udacity-data.com/topher/2023/July/64ac0039_fordgobike-tripdata/fordgobike-tripdata.csv) (39.4 MB): This data set includes information about individual rides made in a bike-sharing system covering the greater San Francisco Bay area.

Note that this dataset will require some data wrangling in order to make it tidy for analysis. There are multiple cities covered by the linked system, and multiple data files will need to be joined together if a full year’s coverage is desired.

Here are some example questions for your analysis. Be creative and think of more such questions.

When are most trips taken in terms of time of day, day of the week, or month of the year?
How long does the average trip take?
Does the above depend on if a user is a subscriber or customer?

#### 1.2. Download Starter Files
To help you get rolling with the project, we've provided two `.zip` folders in the Resources section:
* Project Template - It contains the starter files.
* Example Project - This is a sample submission of the completed project.

#### 1.3. Project Template
The [Project Template](https://video.udacity-data.com/topher/2021/September/6155a869_project-template/project-template.zip) contains the following files that will give you a head start.
* `Part_I_exploration_template.ipynb` - This is your starting point for the project Part I. This file contains multiple sections to help you organize your exploration. At the end of each section, there are questions to help you summarize your findings and reflect on the steps taken through the investigation.
* `Part_II_slide_deck_template.ipynb` - This is your starting point for the project Part II. This file contains starter cells to help you organize your slide-deck deliverable. These cells provide examples of how the slide deck should be organized, including pre-set slideshow settings.
* README.md* - This markdown file contains the following sections that you will fill as you progress through the project.
* Dataset
* Summary of Findings
* Key Insights for Presentation


## Instructions - Part II
### Part 2 - Explanatory Data Visualization
#### 2.1. Update the README.md
As you complete the part I of the project, document your findings in a the README.md file available in the template. Particularly, update these sections in the README.md file:
* __Dataset__ - Introduce your dataset and document its source. Summarise the steps you took in your data exploration.
* __Summary of Findings__ - Summarise your data exploration findings and reflect on the steps you took in your data exploration. Mention whether you plan to bring them into your explanatory presentation or not.
* __Key Insights for Presentation__ - Write about why/how you chose certain findings over others to put in your explanatory analysis. Highlight the key insights that you want to convey in your explanatory report as well as any changes to visualizations, or note new visualizations that will be created to bridge between your insights.

#### 2.2. Generate Explanatory Data Visualizations
Generate explanatory data visualizations to tell a story about the data you explored. Open the `Part_II_slide_deck_template.ipynb` template notebook file and finish these tasks:
* Add a summary of key insights at the start of the notebook, just as you added in the README.md. This will help your notebook to stay aligned to the key insights you want to include in your slide deck.
* Use code that you used in your exploration phase to generate selective and polished plots.
* Make sure that you pay attention to aspects of design integrity in your revisions. Use appropriate plot types, transformations, and encoding. All plots in the presentation should have a title, labeled axes (including units, if any), legend, scale, ticks, and optionally grid in the plot.
* You need to provide at least 3 visualizations to convey key insights, along with descriptive comments which accurately depict their purpose.

#### 2.3. Create Slide Deck
Now it's time to create a slide deck by converting the notebook file. You need to prepare the notebook for conversion using the steps below:
1. __Add Cell Toolbar__ - Add a specific Cell Toolbar to each cell in your notebook. To do this, select a cell and click on View > Cell Toolbar > Slideshow.
2. __Choose Slide Type__ - Assign each cell a Slide Type. Choose `Slide` for the markdown cells that you want to appear in the slide show, for example, the cells that describe your visualizations. For the code cells that display the visualization, you can choose `Sub-Slide`. You can choose `Skip` for the other code cells that don't display visualizations and are not crucial to the presentation.
3. __Convert__ - Once you're ready to generate your presentation, use nbconvert to export the notebook and set up a server for the slides. In the last code cell, use the following command:
```
!jupyter nbconvert <Notebook_name>.ipynb --to slides --post serve --no-input --no-prompt
```
The command above should open a tab in your web browser where you can scroll through your presentation. Sub-slides can be accessed by pressing 'down' when viewing its parent slide. Make sure you remove all of the quote-formatted guide notes in the template before you finish your presentation!

Later you can stop the Kernel.