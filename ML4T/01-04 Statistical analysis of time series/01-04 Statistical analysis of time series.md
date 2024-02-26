#01-04 Statistical analysis of time series

## Are you ready

1. **Professor:** "Are you ready, Dave?"
2. **Dave:** "Ready for what, Professor?"
3. **Professor:** "We're going to start some serious number crunching now."
4. **Dave:** "What do you mean?"
5. **Professor:** "In this lesson, we're going to unleash the power of Python."
6. **Professor:** "We're going to show folks some tools that enable them to calculate all kinds of important statistics on time series data."
7. **Dave:** "What are we waiting for?"
8. **Professor:** "Let's go."

## Global statistics

1. **Introduction to Global Statistics:**

   - The lesson introduces the concept of computing various kinds of statistics on time series data, starting with global statistics.

2. **Example Data Frame:**

   - Reference is made to a data frame named DF1 with columns for SPY, XOM, Google, and Gold. This data frame seems to contain financial data.

3. **Computation of Mean:**

   - It's explained that the mean of each column can be computed easily using a statement provided.

4. **Data Frame Functionality:**

   - The data frame is described as augmenting NumPy and providing additional functionality beyond a basic array.

5. **Available Functions:**

   - Various statistical functions available for use with data frames are mentioned, including mean, median, standard deviation, sum, prod (product), and mode.

6. **Abundance of Statistics:**

   - It's stated that there are at least 33 global statistics that can be computed in this way, with new ones being added over time.

7. **Transition to Demonstrating Code:**
   - The presentation concludes by mentioning that Dave will demonstrate how to perform these computations in code.
     ![2](./images/2.png)

##Compute global statistics

1. **Introduction to Coding Example:**

   - The segment starts with the presenter mentioning they will now demonstrate the concepts explained by the professor through coding.

2. **Defining Symbols List and Building DataFrame:**

   - A list of symbols (presumably representing stocks) is defined, including symbols like SPY, XOM, GOOG, and GLD.
   - A DataFrame named `df` is created using these symbols, similar to previous lessons.

3. **Computing Mean:**

   - The mean of stock prices for each symbol is computed using `dataframe.mean()`.
   - It's emphasized that this single line of code computes the mean for all stocks.

4. **Output Verification:**

   - The output of the mean computation is checked, noting how Pandas properly labels the mean for each symbol.

5. **Graphical Representation:**

   - A graph showing symbols and their corresponding data is mentioned.

6. **Computing Median and Standard Deviation:**

   - Similar to computing the mean, median and standard deviation are computed using `dataframe.median()` and `dataframe.std()` respectively.

7. **Explanation of Mean, Median, and Standard Deviation:**

   - The difference between mean and median is explained.
   - Standard deviation is described mathematically as the square root of variance and intuitively as a measure of deviation from the central value, which is the mean.

8. **Conclusion:**
   - The segment concludes by emphasizing the importance of understanding statistics such as mean, median, and standard deviation in analyzing time series data, especially in assessing the variability of stock prices over time.
     ![3-1](./images/3-1.png)
     ![3=2](./images/3-2.png)

## Rolling statistics

1. **Introduction to Rolling Statistics:**

   - Rolling statistics are described as a new type of statistic involving snapshots over windows rather than across the entire period.
   - They offer a different perspective compared to global statistics.

2. **Explanation of Rolling Mean:**

   - Rolling mean, using a 20-day rolling mean as an example, calculates the mean within a moving window of data.
   - A window moves forward each day, computing the mean of the data within that window.

3. **Characteristics of Rolling Mean:**

   - Rolling mean is depicted as a smoothed and lagged line, reflecting an average of data over the specified window.
   - It contrasts with day-to-day values but provides insights into overall trends.

4. **Application in Technical Analysis:**

   - Rolling mean serves as a technical indicator, known as a simple moving average, in financial analysis.
   - Analysts monitor instances where the price crosses the rolling average, which may signal potential trading opportunities.
   - A hypothesis suggests that significant deviations from the rolling mean could lead to a return to the mean, influencing trading decisions.

5. **Challenges and Considerations:**

   - Determining the significance of deviations from the rolling mean poses a challenge for analysts.
   - It's crucial to assess when deviations warrant attention in trading strategies.

     ![4](./images/4.png)

## Which statistic to use
