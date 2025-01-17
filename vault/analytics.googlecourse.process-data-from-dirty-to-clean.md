---
id: hzz8zbo5j4l0uxsfowtq3il
title: Process Data from Dirty to Clean
desc: ''
updated: 1650679669585
created: 1649638993702
---
> A strong analysis depends on the integrity of the data.

### Data Integrity

The accuracy, completeness, consistency, and trustworthiness of data throughout its lifecycle.

### Data replication

The process of storing data in multiple locations.

If we are replicating data at different times in different places, there is a chance data will be out of sync. This data lacks integrity because different people might not be using same data for their findings.

### Data transfer

The process of copying data from a storage device to memory, or from one computer to another.

If the data transfer faced interruption there might be problem with data used for the analysis.

### Data manipulation

The process of changing data to make it more organized and easier to read.

Unwanted manipulation can break the data integrity.

### Other threats to the data integrity

- Human error
- Viruses(Computer Virus)
- Malware
- Hacking
- System failure


### Data constraints

| Data constraint                     | Definition                                                                                       | Examples                                                                                                                                                                                                                                                     |
| ----------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Data type                           | Values must be of a certain type: date, number, percentage, Boolean, etc.                        | If the data type is a date, a single number like 30 would fail the constraint and be invalid                                                                                                                                                                 |
| Data range                          | Values must fall between predefined maximum and minimum values                                   | If the data range is 10-20, a value of 30 would fail the constraint and be invalid                                                                                                                                                                           |
| Mandatory                           | Values can’t be left blank or empty                                                              | If age is mandatory, that value must be filled in                                                                                                                                                                                                            |
| Unique                              | Values can’t have a duplicate                                                                    | Two people can’t have the same mobile phone number within the same service area                                                                                                                                                                              |
| Regular expression (regex) patterns | Values must match a prescribed pattern                                                           | A phone number must match ###-###-#### (no other characters allowed)                                                                                                                                                                                         |
| Cross-field validation              | Certain conditions for multiple fields must be satisfied                                         | Values are percentages and values from multiple fields must add up to 100%                                                                                                                                                                                   |
| Primary-key                         | (Databases only) value must be unique per column                                                 | A database table can’t have two rows with the same primary key value. A primary key is an identifier in a database that references a column in which each value is unique. More information about primary and foreign keys is provided later in the program. |
| Set-membership                      | (Databases only) values for a column must come from a set of discrete values                     | Value for a column must be set to Yes, No, or Not Applicable                                                                                                                                                                                                 |
| Foreign-key                         | (Databases only) values for a column must be unique values coming from a column in another table | In a U.S. taxpayer database, the State column must be a valid state or territory with the set of acceptable values defined in a separate States table                                                                                                        |
| Accuracy                            | The degree to which the data conforms to the actual entity being measured or described           | If values for zip codes are validated by street location, the accuracy of the data goes up.                                                                                                                                                                  |
| Completeness                        | The degree to which the data contains all desired components or measures                         | If data for personal profiles required hair and eye color, and both are collected, the data is complete.                                                                                                                                                     |
| Consistency                         | The degree to which the data is repeatable from different points of entry or collection          | If a customer has the same address in the sales and repair databases, the data is consistent.                                                                                                                                                                |

> It's important check that the data you use aligns with the business objective.

### Well-aligned objectives and data

You can gain powerful insights and make accurate conclusions when data is well-aligned to business objectives. As a data analyst, alignment is something you will need to judge. Good alignment means that the data is relevant and can help you solve a business problem or determine a course of action to achieve a given business objective.

```code
Alignment to business objective + newly discovered variables + constraints = accurate conclusions
```

### Dealing with insufficient data

Types of insufficient data

- Data from only one source
- Data that keeps updating
- Outdated data
- Geographically limited data

Ways to address insufficient data

- Identify the trends with the available data
- Wait for more data if time allows
- Talk with stakeholders and adjust your objective
- Look for a new dataset

### What to do when you find an issue with your data

#### Data issue 1: no data

| Possible Solutions                                                                                                                                               | Examples of solutions in real life                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gather the data on a small scale to perform a preliminary analysis and then request additional time to complete the analysis after you have collected more data. | If you are surveying employees about what they think about a new performance and bonus plan, use a sample for a preliminary analysis. Then, ask for another 3 weeks to collect the data from all employees. |
| If there isn’t time to collect data, perform the analysis using proxy data from other datasets.  _This is the most common workaround._                           | If you are analyzing peak travel times for commuters but don’t have the data for a particular city, use the data from another city with a similar size and demographic.                                     |

#### Data issue 2: too little data

| Possible Solutions                                            | Examples of solutions in real life                                                                                                                                                |
| ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Do the analysis using proxy data along with actual data.      | If you are analyzing trends for owners of golden retrievers, make your dataset larger by including the data from owners of Labradors.                                             |
| Adjust your analysis to align with the data you already have. | If you are missing data for 18- to 24-year-olds, do the analysis but note the following limitation in your report: _this conclusion applies to adults 25 years and older_ _only_. |

#### Data issue 3: wrong data, including data with errors*

| Possible Solutions                                                                                                                                                                                   | Examples of solutions in real life                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| If you have the wrong data because requirements were misunderstood, communicate the requirements again.                                                                                              | If you need the data for female voters and received the data for male voters, restate your needs.                                                                                                 |
| Identify errors in the data and, if possible, correct them at the source by looking for a pattern in the errors.                                                                                     | If your data is in a spreadsheet and there is a conditional statement or boolean causing calculations to be wrong, change the conditional statement instead of just fixing the calculated values. |
| If you can’t correct data errors yourself, you can ignore the wrong data and go ahead with the analysis of your sample size is still large enough and ignoring the data won’t cause systematic bias. | If your dataset was translated from a different language and some translations don’t make sense, ignore the data with bad translation and go ahead with the analysis of the other data.    |

![Data Errors](/assets/images/2022-04-12-06-41-49.png)

### The importance of sample size

### Population size

All possible data values in certain dataset

### Sample size

A part of population that is representative of the population

**Downside of the sample size:** When the population itself small, then the sample form that population might be less effective. This might lead to Sampling bias.

### Sampling bias

A sample isn't representative of the population as a whole.

### Random sampling

Using random sampling can reduce some issues with the sampling bias.

A way of selecting a sample from a population so that every possible type of the sample has an equal chance of being chosen.

| Terminology              | Definitions                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Population               | The entire group that you are interested in for your study. For example, if you are surveying people in your company, the population would be all the employees in your company.                                                                                                                                                                                                     |
| Sample                   | A subset of your population. Just like a food sample, it is called a sample because it is only a taste. So if your company is too large to survey every individual, you can survey a representative sample of your population.                                                                                                                                                       |
| Margin of error          | Since a sample is used to represent a population, the sample’s results are expected to differ from what the result would have been if you had surveyed the entire population. This difference is called the margin of error. The smaller the margin of error, the closer the results of the sample are to what the result would have been if you had surveyed the entire population. |
| Confidence level         | How confident you are in the survey results. For example, a 95% confidence level means that if you were to run the same survey 100 times, you would get similar results 95 of those 100 times. Confidence level is targeted before you start your study because it will affect how big your margin of error is at the end of your study.                                             |
| Confidence interval      | The range of possible values that the population’s result would be at the confidence level of the study. This range is the sample result +/- the margin of error.                                                                                                                                                                                                                    |
| Statistical significance | The determination of whether your result could be due to random chance or not. The greater the significance, the less due to chance.                                                                                                                                                                                                                                                 |

When figuring out a sample size, here are things to keep in mind:

- Don’t use a sample size less than 30. It has been statistically proven that 30 is the smallest sample size where an average result of a sample starts to represent the average result of a population.
- The confidence level most commonly used is 95%, but 90% can work in some cases.

Increase the sample size to meet specific needs of your project:

- For a higher confidence level, use a larger sample size
- To decrease the margin of error, use a larger sample size
- For greater statistical significance, use a larger sample size

### Using statistical power

**Statistical power:** The probability of getting meaningful results from a hypothesis test

**Hypothesis testing:** A way to see if a survey or experiment has meaningful results

If a test is statistically significant, it means the results of the test are real and not an error caused by the random chance.

Usually, you need a statistical power if at least 0.8 or 80% to consider your results statistically significant.

CSV, J​SON, SQLite, and BigQuery datasets

- [credit-card-customers](https://www.kaggle.com/sakshigoyal7/credit-card-customers)
- [You-tube-trends](https://www.kaggle.com/datasnaek/youtube-new)
- [us-wildfires](https://www.kaggle.com/rtatman/188-million-us-wildfires)
- [google-analytics-sample<](https://www.kaggle.com/bigquery/google-analytics-sample)

### Determine the sample size

### Confidence level

The probability that your sample size accurately reflects the greater population.

Having 99% confidence level is ideal, but most industries hope for at least a 90% or 95% confidence level.

### Margin of error

Margin of errors is the difference between the sample result and the population result.

(or)

The maximum amount that the sample results is expected to differ from those of the actual population.

$$MOE_\gamma = z_\gamma \times \sqrt{\frac{\sigma^2}{n}}$$

where $z_\gamma$ is the z-score, $n$ is the sample size, and $\sigma^2$ is the variance of the population.
variance: $\sigma^2=\frac{\sum(x_i-\bar x)^2}{n-1}$

The z-score is the difference between the sample result and the population result divided by the standard deviation of the population.

$z=\frac{x-\mu}{\sigma}$

where:
μ is the mean of the population,
σ is the standard deviation of the population.

Calculating z using this formula requires use of the population mean and the population standard deviation, not the sample mean or sample deviation. However, knowing the true mean and standard deviation of a population is often an unrealistic expectation, except in cases such as standardized testing, where the entire population is measured.

When the population mean and the population standard deviation are unknown, the standard score may be estimated by using the sample mean and sample standard deviation as estimates of the population values.

$$z=\frac{x-\bar x}{\sigma}$$

Where $x$ is the sample result, $\bar x$ is the population result, and $\sigma$ is the standard deviation of the population.

Example [^1]: A market research agency conducted a survey to identify how many mobile phone users use their devices to access social media. They surveyed 1000 mobile phone users and found that 540 regularly used their devices to access their social media profiles.

[^Reference]: https://goodcalculators.com/

Let's assume that we require a 95% level of confidence; as such, the z-score = 1.96.

The sample population, p, is 540 / 1000 = 0.54. (The sample size, n, was 1000.)

As such, the margin of error in this survey is as follows:

$$MOE=z\times\frac{\sqrt{p\times(1-p)}}{\sqrt{n}}$$

MOE  is the margin of error,

z is the z-score associated with a level of confidence,

p is the sample proportion, expressed as a decimal,

n is the sample size,

$$MOE=1.96\times\frac{\sqrt{0.54\times(1-0.54)}}{\sqrt{1000}}$$

$$MOE=\frac{0.977}{31.623}\times100=3.089%$$

These results indicate that the market research company can conclude with 95% confidence that 54% of mobile phone users use their device to access social media, give or take 3%.

### Estimated response rate

If you are running a survey of individuals, this is the percentage of people you expect will complete your survey out of those who received the survey.

### Sample size calculators

In order to use a sample size calculator, you need to have the [[Sample size|analytics.googlecourse.process-data-from-dirty-to-clean#sample-size]], [[Confidence level|analytics.googlecourse.process-data-from-dirty-to-clean#confidence-level]], and the acceptable [[Margin of error|analytics.googlecourse.process-data-from-dirty-to-clean#margin-of-error]] already decided, so you can input them into the tool. If this information is ready to go, check out these sample size calculators below:

- [Sample Size Calculator: Understanding Sample Sizes | SurveyMonkey](https://www.surveymonkey.com/mp/sample-size-calculator/)
- [Sample Size Calculator by Raosoft, Inc.](http://www.raosoft.com/samplesize.html)

After you have plugged your information into one of these calculators, it will give you a recommended sample size. Keep in mind, the calculated sample size is the minimum number to achieve what you input for confidence level and margin of error. If you are working with a survey, you will also need to think about the estimated response rate to figure out how many surveys you will need to send out. For example, if you need a sample size of 100 individuals and your estimated response rate is 10%, you will need to send your survey to 1,000 individuals to get the 100 responses you need for your analysis.

### Data Cleaning

### Dirty Data

Data that is incomplete, incorrect, or irrelevant to the problem you're trying to solve.

Types of dirty data:

![Types of dirty data](/assets/images/2022-04-15-06-53-36.png)

### Clean Data

Data that is complete, correct, and relevant to the problem you're trying to solve.

### Data engineers

Transform data into a useful a format for analysis and give it a reliable infrastucrure.

### Data warehousing specialists

Develope processess and prcedures to effectively store and organize data.

### Null

An indication that a value does not exist in a dataset.

### Recognize and remedy dirty data

### Data validation

A tool for checking the accuracy and qualatity of data before adding or importing it.

### Merger

An agreement that unites two organizaton into single new one.

Questions before merge two datasets

- Do I have all the data I need?
- Does the data I need exists within these datasets?
- Does the data need to be cleaned, or are they ready for me to use?
- Are the datasets cleaned to the same standard.

### Data compatability

How well two are nore datasets are able to work together.

### Common data-cleaning pitfalls

Some of the errors you might come across while cleaning your data could include:

![common data-cleaning pitfalls](/assets/images/2022-04-15-07-31-43.png)

Refer to these "top ten" lists for data cleaning in Microsoft Excel and Google Sheets to help you avoid the most common mistakes:

- [Top ten ways to clean your data](https://support.microsoft.com/en-us/office/top-ten-ways-to-clean-your-data-2844b620-677c-47a7-ac3e-c2e157d1db19)
- [10 Google Workspace tips to clean up data - Google Workspace Learning Center](https://support.google.com/a/users/answer/9604139?hl=en#zippy=)


### Data cleaning features in spereadsheets

### Conditonal formatting

A spreedsheet tool that changes how cells apprear when values meet specific conditions.

### Remove duplicates

A tool that automatically searches for and eliminates duplicate entries from a spreadsheet.

### Split

A tool that divides text around a specified character or string and put each fragment into a new, seperate cell.

### Concatenate

A function that joins multiple text strings into a single string.

### Optimizing the data-cleaning process

### Shpreadsheet functions

A set of instructions that perform a specific calculation using the data in a spreadsheet.

### Syntax

A predetermine set of instructions that perform a specific calculation using the data in a spreadsheet.

### COUNTIF

A function that returns the number of cells that match a specified value.

```code
=COUNTIF(range, "value")
```

### LEN

A function that returns the length of a text string.

```code
=LEN(text)
```

### LEFT

A function that gives you a set number of characters from the left side of a text string.

```code
=LEFT(text, number of characters)
```

### RIGHT

A function that gives you a set number of characters from the right side of a text string.

```code
=RIGHT(text, number of characters)
```

### MID

A function that gives you a segment from the middle of a text string.

```code
=MID(text, start, number of characters)
```

### CONCATENATE

A function that joins together multiple text strings into a single string.

```code
=CONCATENATE(text1, text2, text3, ...)
```

### TRIM

A function that removes leading and trailing spaces from a text string.

```code
=TRIM(text)
```

### Workflow automation

- [Automating Scientific Data Analysis Part 1:](https://towardsdatascience.com/automating-scientific-data-analysis-part-1-c9979cd0817e)
- [Automating big-data analysis](https://news.mit.edu/2016/automating-big-data-analysis-1021)
- [10 of the Best Options for Workflow Automation Software](https://technologyadvice.com/blog/information-technology/top-10-workflow-automation-software/)

### Different data perspectives

### VLOOKUP

A function that searches for a certain value in a column to return a corresponding peiece of information.

```code
=VLOOKUP(data to lookup, 'where to look'!Range, column, [match type])
```

### Data mapping

The process of matching fields from one data source to another.

### Compatibility

How well two are more datasets are able to work together.

### Using SQL to clean data

SQL is the primary way data analysts extract data from databases.

Spreadsheets and SQL both have their advantages and disadvantages:

| Features of Spreadsheets                             | Features of SQL Databases                                          |
| ---------------------------------------------------- | ------------------------------------------------------------------ |
| Smaller data sets                                    | Larger datasets                                                    |
| Enter data manually                                  | Access tables across a database                                    |
| Create graphs and visualizations in the same program | Prepare data for further analysis in another software              |
| Built-in spell check and other useful functions      | Fast and powerful functionality                                    |
| Best when working solo on a project                  | Great for collaborative work and tracking queries run by all users |

### SQL dialects and their uses

- [What Is a SQL Dialect, and Which one Should You Learn?](https://learnsql.com/blog/what-sql-dialect-to-learn/)
- [Difference Between SQL Vs MySQL Vs SQL Server (with Examples)](https://www.softwaretestinghelp.com/sql-vs-mysql-vs-sql-server/)
- [SQL Server, PostgreSQL, MySQL... what's the difference? Where do I start?](https://www.datacamp.com/community/blog/sql-differences)
- [SQLite Windows Functions](https://sqlite.org/windowfunctions.html)
- [What is SQL](https://www.sqltutorial.org/what-is-sql/)

### Understand how data is measured

Data is measured by the number of bits it takes to represent it. All information in a computer can be represented as a binary number consisting solely of 0’s and 1’s. Each 0 or 1 in a number is a bit. A bit is the smallest unit of storage in computers. Since computers work in binary (Base 2), this means that all the important numbers that differentiate between different data sizes will be powers of 2.

A byte is a collection of 8 bits. Take a moment to examine the table below to get a feel for the difference between data measurements and their relative sizes to one another.

| Unit      | Equivalent to  | Abbreviation | Real-World Example                             |
| --------- | -------------- | ------------ | ---------------------------------------------- |
| Byte      | 8 bits         | B            | 1 character in a string                        |
| Kilobyte  | 1024 bytes     | KB           | A page of text (~4 kilobytes)                  |
| Megabyte  | 1024 Kilobytes | MB           | 1 song in MP3 format (~2-3 megabytes)          |
| Gigabyte  | 1024 Megabytes | GB           | ~300 songs in MP3 format                       |
| Terabyte  | 1024 Gigabytes | TB           | ~500 hours of HD video                         |
| Petabyte  | 1024 Terabytes | PB           | 10 billion Facebook photos                     |
| Exabyte   | 1024 Petabytes | EB           | ~500 million hours of HD video                 |
| Zettabyte | 1024 Exabytes  | ZB           | All the data on the internet in 2019 (~4.5 ZB) |

### Widely used SQL queries

```sql
SELECT col1, col2 FROM table_name;
```

```sql
INSERT INTO table_name (col1, col2) VALUES (value1, value2);
```

```sql
UPDATE table_name SET col1 = value1, col2 = value2 WHERE condition;
```

```sql
DELETE FROM table_name WHERE condition;
```

```sql
CREATE TABLE IF NOT EXISTS table_name (col1 INT, col2 INT);
```

```sql
DROP TABLE IF EXISTS table_name;
```

### Cleaning String variables using sql

```sql
SELECT DISTINCT(col1) FROM table_name;
```

```sql
SELECT LENGTH(col1) AS col1_len FROM table_name;
```

```sql
SELECT col1 FROM table_name WHERE LENGTH(col1) > Integer;
```

```sql
SELECT DISTINCT(col1) FROM table_name WHERE SUBSTR(col1, Integer, Integer) = String;
```

```sql
SELECT DISTINCT(col1) FROM table_name WHERE TRIM(col1) = String;
```

### CAST

Can be used to convert anything from one data type to another.

```sql
SELECT CAST(col1 AS INT) FROM table_name;
```

### CONCAT

Adds strins together ti create new text strings that cab be used as unique keys.

```sql
SELECT CONCAT(col1, col2) FROM table_name;
```

### COALESCE

Can be used to return non-null values in a list.

```sql
SELECT COALESCE(col1, col2) FROM table_name;
```

### Verification

A processs to confirm that a data-cleaning effor was well-executed and the resulting data is accurate and reliable.

### Changelog

A file containing a chronologically oredered list of modifications made to a project.

### See the bigger picture when verifying data-cleaning

1. Consider the business problem
2. Consider the goal
3. Consider the data

### Data-cleaning verification: A checklist

- **Sources of errors:** Did you use the right tools and functions to find the source of the errors in your dataset?
- **Null data:** Did you search for NULLs using conditional formatting and filters?
- **Misspelled words:** Did you locate all misspellings?
that your numeric data has been entered correctly?
- **Extra spaces and characters:** Did you remove any extra spaces or characters using the TRIM function?
- **Duplicates:** Did you remove duplicates in spreadsheets using the Remove Duplicates function or DISTINCT in SQL?
- **Mismatched data types:** Did you check that numeric, date, and string data are typecast correctly?
- **Messy (inconsistent) strings:** Did you make sure that all of your strings are consistent and meaningful?
- **Messy (inconsistent) date formats:** Did you format the dates consistently throughout your dataset?
- **Misleading variable labels (columns):** Did you name your columns meaningfully?
- **Truncated data:** Did you check for truncated or missing data that needs correction?
- **Business Logic:** Did you check that the data makes sense given your knowledge of the business?

![Review the goal of your project](/assets/images/2022-04-23-07-12-12.png)

### Capturing cleaning changes

### Documentation

The process of tracking changes, additions, deletions, and errors involved in your data-cleaning effort.

- Recover data-cleaning errors
- Infrom other users of changes
- Determine quality of data

### Best practices for changelogs

A changelog for a personal project may take any form desired. However, in a professional setting and while collaborating with others, readability is important. These guiding principles help to make a changelog accessible to others:

- Changelogs are for humans, not machines, so write legibly.
- Every version should have its own entry.
- Each change should have its own line.
- Group the same types of changes. For example, Fixed should be grouped separately from Added.
- Versions should be ordered chronologically starting with the latest.
- The release date of each version should be noted.

All the changes for each category should be grouped together. Types of changes usually fall into one of the following categories:

- **Added:** new features introduced
- **Changed:** changes in existing functionality
- **Deprecated:** features about to be removed
- **Removed:** features that have been removed
- **Fixed:** bug fixes
- **Security:** lowering vulnerabilities

```markdown
# Sample Changelog
This file contains the notable changes to the project

Version 1.0.0 (23-04-2022)
## New
    - Added column classifiers (Date, Time, PerUnitCost, TotalCost, etc. )
    - Added Column “AveCost” to track average item cost

## Changes
    - Changed date format to DD-MM-YYYY
    - Removal of whitespace (cosmetic)

## Fixes
    - Fixed misalignment in Column "TotalCost" where some rows did not match with correct dates
    - Fixed SUM to run over entire column instead of partial
```
