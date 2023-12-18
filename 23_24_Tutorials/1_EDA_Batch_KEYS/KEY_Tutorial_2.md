# KEY - EDA with Numerical Data
Mr. Adams

- [EDA with Numerical Data!](#eda-with-numerical-data)
- [By the end of this tutorial I should be able
  to…](#by-the-end-of-this-tutorial-i-should-be-able-to)
  - [1: Load the proper libraries before I start exploring the
    data.](#load-the-proper-libraries-before-i-start-exploring-the-data.)
    - [1.1: Tasks and Questions](#tasks-and-questions)
  - [2: View the data](#view-the-data)
    - [2.1: Tasks and Questions](#tasks-and-questions-1)
    - [2.2: Tasks and Questions](#tasks-and-questions-2)
  - [3: Build a histogram.](#build-a-histogram.)
    - [3.1: Tasks and Questions](#tasks-and-questions-3)
    - [3.2: Tasks and Questions](#tasks-and-questions-4)
  - [4: Build a density curve.](#build-a-density-curve.)
    - [4.1: Tasks and Questions](#tasks-and-questions-5)
  - [5: Generate summary statistics to support a histogram and density
    curve.](#generate-summary-statistics-to-support-a-histogram-and-density-curve.)
    - [5.1: Tasks and Questions](#tasks-and-questions-6)
  - [6: Adjust histogram to include some data visualization best
    practices.](#adjust-histogram-to-include-some-data-visualization-best-practices.)
    - [6.1: Adding Labels](#adding-labels)
    - [6.2: Adjusting Bins](#adjusting-bins)
    - [6.3: Adjusting Scales](#adjusting-scales)
    - [6.4: Clean Up](#clean-up)
    - [6.5: Fill the Bars and Add Color](#fill-the-bars-and-add-color)
    - [6.6: Put it all together.](#put-it-all-together.)
    - [7 Bonus:](#bonus)

# EDA with Numerical Data!

You’ve just finished one tutorial that got your wheels turning! If that
was your first time writing code, congrats on taking the dive into an
exciting new challenge!

Over the past few weeks, you’ve built an understanding of the types of
visualizations you can create, the statistics you can generate to
support those visualizations, and how to interpret both. With that
strong foundation laid down, you are now ready to explore real data to
begin uncovering the stories hidden within them.

# By the end of this tutorial I should be able to…

## 1: Load the proper libraries before I start exploring the data.

For this tutorial, we will use three packages: `tidyverse`, `openintro`,
and `skimr`.

`Tidyverse` is made up of a collection of packages that include tools
making it easier to visualize, summarize, and wrangle data.

`Openintro` is a package referenced in our textbook, Introduction to
Modern Statistics. Among other things, it includes a number of datasets.
During this tutorial, you will generate similar visualizations to those
seen when reading.

`Skimr` is a package that will help us quickly generate summary
statistics.

### 1.1: Tasks and Questions

1.  Run the following code.

``` r
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
    ✔ purrr     1.0.2     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(openintro)
```

    Loading required package: airports
    Loading required package: cherryblossom
    Loading required package: usdata

``` r
library(skimr)
```

## 2: View the data

For this tutorial, we will use the dataset titled `loan50` provided in
the `openintro` package. You first read about this dataset in [Chapter 1
of Introduction to Modern
Statistics](https://openintro-ims.netlify.app/data-hello#data-basics).

The data in `loan50` includes 50 randomly sampled loans offered through
Lending Club, which is a peer-to-peer lending company.

Again, the Name_of_the_Dataset is `loan50`.

### 2.1: Tasks and Questions

1.Run the following code to view the data.

``` r
view(loan50)
```

2.  Run the following code to get a glimpse of the data.

``` r
glimpse(loan50)
```

    Rows: 50
    Columns: 18
    $ state                   <fct> NJ, CA, SC, CA, OH, IN, NY, MO, FL, FL, MD, HI…
    $ emp_length              <dbl> 3, 10, NA, 0, 4, 6, 2, 10, 6, 3, 8, 10, 10, 2,…
    $ term                    <dbl> 60, 36, 36, 36, 60, 36, 36, 36, 60, 60, 36, 36…
    $ homeownership           <fct> rent, rent, mortgage, rent, mortgage, mortgage…
    $ annual_income           <dbl> 59000, 60000, 75000, 75000, 254000, 67000, 288…
    $ verified_income         <fct> Not Verified, Not Verified, Verified, Not Veri…
    $ debt_to_income          <dbl> 0.55752542, 1.30568333, 1.05628000, 0.57434667…
    $ total_credit_limit      <int> 95131, 51929, 301373, 59890, 422619, 349825, 1…
    $ total_credit_utilized   <int> 32894, 78341, 79221, 43076, 60490, 72162, 2872…
    $ num_cc_carrying_balance <int> 8, 2, 14, 10, 2, 4, 1, 3, 10, 4, 3, 4, 3, 2, 3…
    $ loan_purpose            <fct> debt_consolidation, credit_card, debt_consolid…
    $ loan_amount             <int> 22000, 6000, 25000, 6000, 25000, 6400, 3000, 1…
    $ grade                   <fct> B, B, E, B, B, B, D, A, A, C, D, A, A, A, A, E…
    $ interest_rate           <dbl> 10.90, 9.92, 26.30, 9.92, 9.43, 9.92, 17.09, 6…
    $ public_record_bankrupt  <int> 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0…
    $ loan_status             <fct> Current, Current, Current, Current, Current, C…
    $ has_second_income       <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALS…
    $ total_income            <dbl> 59000, 60000, 75000, 75000, 254000, 67000, 288…

**Are you confused? I certainly would be!** Before diving into any
exploration, you need to first be sure you understand the data

3.  Click this link
    <https://www.openintro.org/data/index.php?data=loan50> to learn more
    about this dataset.

**For the next five questions, use information from the link you just
read and the code your ran in questions 1 and 2 of this section.**

4.  From what platform was this data taken?

    Lending Club

5.  What does that platform do?

    Lending Club is an online platform this makes it possible for people
    to lend to one another.

6.  What are the observational units in the `loan50` dataset?

    The observational units are loans given out on Lending Club.

7.  How many observations are there?

    There are 50 observations. In other words, this dataset includes
    information about 50 loans.

8.  How many variables are there?

    There are 18 variables, which are a mix of numerical and categorical
    variables.

***For the rest of this tutorial, you will work with a smaller version
of this data set. We’ll keep the 50 rows, but select 7 of the 18
variables we started with.***

9.  Run the code below makes this new and smaller data frame.

``` r
loan50_small <- loan50 |>
                select(loan_amount, interest_rate, term, grade, 
                       state, total_income, homeownership)
```

### 2.2: Tasks and Questions

1.  What is the name of the new data frame created in the lines of code
    above? Type the name EXACTLY how it appears above. (Hint: Copying
    and pasting is your friend! Also, if you double click on text it
    will highlight it for you. Give it a try!)

    `loan50_small`

2.  What is the name of this symbol \|\> ?

    This is called a pipe.

3.  When you are reading code and come across the symbol \|\> you should
    say, “And \_\_\_\_\_\_”

    And then

4.  List all of the numerical variables? Type the names EXACTLY how they
    appear in the code above. *Hint: Copying and pasting is your
    friend!*

    `loan_amount`, `interest_rate`, `total_income`

## 3: Build a histogram.

Throughout this year, you’ve learned how to ask statistical questions
and choose the visualizations and statistics that will allow you to
begin answering those questions.

Your process of doing those things has gone something like…

To answer this question I…

- need this data frame

- specifically need this variable

- need to put it on the blank axis

- and I want to make this visualization.

Fortunately, the structure of the code you will write to create
visualizations in R follows this same structure.

The code below reads like this…

- Use the Name_of_Data_Frame AND THEN

- Make a plot with the following aesthetics: the x-axis is this
  Numerical_Variable and ADD

- A histogram.

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram()
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](KEY_Tutorial_2_files/figure-commonmark/example%20histogram-1.png)

### 3.1: Tasks and Questions

1.  Run the code above.

2.  What is a question that could be explored with the histogram created
    by the code above?

    What size loans tend to be given out on Lending Club?

3.  Describe the shape of the distribution and what that tells you about
    the loan amounts.

    The distribution of loans is skewed to the right, meaning that most
    loans are less than \$20,000 while a small number of loans are
    \$30,000 or more.

### 3.2: Tasks and Questions

1.  Write a question that could be answered by creating a histogram
    using the data frame named `loan50_small`. *(use a different
    variable than the one used in 3.1)*  
    What is the typical income of someone taking a loan out on Lending
    Club?

2.  What is the numerical variable you’ll need to use to create the
    histogram. Write the name EXACTLY as it appears in the data frame.

    `total_income`

3.  In the code below, replace `NAME_OF_DATA_FRAME` with loan50_small.

4.  In the code below, replace `NUMERICAL_VARIABLE` with the name you
    wrote in question 2 and then run the chunk of code.

5.  Describe the distribution. Be sure to comment on the shape, center,
    and spread of the distribution.

    The interest rates on Lending Club loans tend to fall below 11%. The
    median interest appears to be 10%. The distribution in skewed to the
    right, which means that while many of interest rates are below 11%,
    there are a few loans that had interest rates of 20 to 28 percent.

``` r
loan50_small |>
  ggplot(aes(x = total_income)) +
  geom_histogram()
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](KEY_Tutorial_2_files/figure-commonmark/your%20first%20histogram-1.png)

## 4: Build a density curve.

### 4.1: Tasks and Questions

1.  Copy the code you wrote to create the histogram in section 3.2 and
    paste it into the gray section below.

2.  If you are about to change your visualization from a histogram to a
    density curve, will you need to change the variable listed on the
    x-axis?

    No you don’t because we are still looking to visualize the
    distribution of loan amounts.

3.  In the code below, change `geom_histogram()` to `geom_density()` and
    then run the entire code chuck.

    ``` r
    loan50_small |>
      ggplot(aes(x = total_income)) +
      geom_density()
    ```

    ![](KEY_Tutorial_2_files/figure-commonmark/your%20first%20density%20curve-1.png)

4.  Bonus: True or False - You can create a density curve for a discrete
    numeric variable. (Explain your answer)

    False. A discrete numeric variable can only take on distint numbers
    yet a density curve shows a continuous spectrum of numbers.
    Therefore, density curves can be used with a continuous numeric
    variable, like loan amount.

## 5: Generate summary statistics to support a histogram and density curve.

As we’ve talked about a number of times in class, let the computer do
the work when it comes to calculations. You won’t pull out your ti
calculator or a piece of paper to calculate statistics for large
datasets.

The organization of your code to perform these calculations goes like
this…

- Look at this data AND THEN

- select this/these variable(s) AND THEN

- generate the summary statistics

Below is the code to generate the summary statistics for the histogram I
created.

``` r
loan50_small |>
  select(loan_amount) |>
  skim()
```

|                                                  |                            |
|:-------------------------------------------------|:---------------------------|
| Name                                             | select(loan50_small, loan… |
| Number of rows                                   | 50                         |
| Number of columns                                | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                            |
| Column type frequency:                           |                            |
| numeric                                          | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                            |
| Group variables                                  | None                       |

Data summary

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |  mean |       sd |   p0 |  p25 |   p50 |   p75 |  p100 | hist  |
|:--------------|----------:|--------------:|------:|---------:|-----:|-----:|------:|------:|------:|:------|
| loan_amount   |         0 |             1 | 17083 | 10455.46 | 3000 | 7125 | 15500 | 24000 | 40000 | ▇▅▆▂▂ |

### 5.1: Tasks and Questions

1.  Write the code that would generate the summary statistics that could
    be used to help answer the questions you wrote in 3.2. Hint: Copy
    and Paste is your friend!

``` r
loan50_small |>
  select(total_income) |>
  skim()
```

|                                                  |                            |
|:-------------------------------------------------|:---------------------------|
| Name                                             | select(loan50_small, tota… |
| Number of rows                                   | 50                         |
| Number of columns                                | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                            |
| Column type frequency:                           |                            |
| numeric                                          | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                            |
| Group variables                                  | None                       |

Data summary

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |     mean |       sd |    p0 |   p25 |   p50 |    p75 |   p100 | hist  |
|:--------------|----------:|--------------:|---------:|---------:|------:|------:|------:|-------:|-------:|:------|
| total_income  |         0 |             1 | 105220.6 | 68141.97 | 28800 | 60000 | 78750 | 119000 | 325000 | ▇▃▂▁▁ |

2.  Copy and Paste the code for your histogram and your summary stats
    into the space below.

3.  Run the code.

``` r
loan50_small |>
  ggplot(aes(x = total_income)) +
  geom_histogram()
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](KEY_Tutorial_2_files/figure-commonmark/viz%20and%20stats-1.png)

``` r
loan50_small |>
  select(total_income) |>
  skim()
```

|                                                  |                            |
|:-------------------------------------------------|:---------------------------|
| Name                                             | select(loan50_small, tota… |
| Number of rows                                   | 50                         |
| Number of columns                                | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |                            |
| Column type frequency:                           |                            |
| numeric                                          | 1                          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |                            |
| Group variables                                  | None                       |

Data summary

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |     mean |       sd |    p0 |   p25 |   p50 |    p75 |   p100 | hist  |
|:--------------|----------:|--------------:|---------:|---------:|------:|------:|------:|-------:|-------:|:------|
| total_income  |         0 |             1 | 105220.6 | 68141.97 | 28800 | 60000 | 78750 | 119000 | 325000 | ▇▃▂▁▁ |

4.  Describe the distribution of the numerical variable you choose when
    creating the data visualization. Be sure to comment on the shape,
    center, and spread of the distribution using statistical vocabulary
    you have learned in this class and the appropriate statistics you
    generated.

      
    The distribution of total income for folks getting loans on Lending
    Club is skewed to the right with total incomes tending to be around
    \$78,750. The middle 50% of total incomes range from \$60,000 to
    \$119,000. While 75% of folks getting a loan have incomes less that
    \$119,000, just 5 people have incomes over \$200,000.

## 6: Adjust histogram to include some data visualization best practices.

You may be saying to yourself, “Those histograms didn’t look that great
and were poorly labeled.” If you said something like that, you are
correct.

### 6.1: Adding Labels

In this section, we will add on various **layers** to our code to adjust
different aspects of the visualization.

Let’s start by adding a title, subtitle, and labels to each axis of the
*first histogram made in this tutorial*. Notice in the code below how
the first four lines are the exact same as what we started with above.
To add labels to our visualization, we use `labs`.

#### 6.1: Tasks and Questions

1.  Add a title, subtitle, and labels for each axis by typing in between
    each `""`.

2.  Run the code chunk

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram() +
  labs(
    title ="What size loans to people get at Lending Club?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Loan Amount ($)",
    y = "Number of Loans"
  )
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](KEY_Tutorial_2_files/figure-commonmark/add%20labels%20to%20my%20histogram-1.png)

### 6.2: Adjusting Bins

Since you’ve calculated the summary statistics above you know the loan
amounts have a large range. Also, when looking at the visualization,
it’s not clear as to what the bin width is. When choosing a bin width,
it’s important to **choose one that is relevant**. Also, the bin width
should help to create a visualization that does not either oversimplify
the distribution or create unnecessary clutter. Certainly, those last
two statements are not very definitive. This is where the creativity and
clear and effective communication come into play.

In the code below, you will see that there is NOT a new layer. We added
an **element** to the histogram so it adjusts the bin width.

#### 6.2: Tasks and Questions

1.  What bin width do you think will be best for the histogram showing
    the distribution of loan amounts? (see histogram and statistics)

    2500

2.  Write the number you choose in question 1 after `binwidth =` in the
    code below.

3.  Write in the title, subtitle, and labels for each axis into the code
    below.

4.  Run the chunk of code.

5.  After running it, adjust the binwidth to a value that you think
    creates the best possible histogram.

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram(binwidth = 2500)+
  labs(
    title ="What size loans to people get at Lending Club?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Loan Amount ($)",
    y = "Number of Loans"
  )
```

![](KEY_Tutorial_2_files/figure-commonmark/adjust%20the%20bins-1.png)

### 6.3: Adjusting Scales

You may also want to adjust the **scales** on the x and y axes.

Be careful when adjusting scales!! Do not distort the story being told!
Whole books are written about topics like this so we’ll talk more about
this as we continue to build visualizations.

A good general rule, keep it simple!

#### 6.3: Tasks and Questions

1.  Copy the code used to generate the histogram in 6.2 Tasks and
    Questions \#5 and paste it into the gray space below.

2.  When you have a continuous variable on the x-axis, you can use the
    following to adjust the scale:

`scale_x_continuous(limits = c(0, 45000), breaks = seq(0, 45000, 5000))`

Edit the words min, max, and ticks in the code you see in the previous
line. min = minimum value for x-axis max = maximum value for x-axis
ticks = where you want the markings along the x-axis.

3.  Put a `+` at the end of the code you pasted into the section below
    and then jump to the next line.

4.  Paste the scale_x_continuous code you adjusted into the last row of
    the code chunk below.

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram(binwidth = 2500)+
  labs(
    title ="What size loans to people get at Lending Club?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Loan Amount ($)",
    y = "Number of Loans"
  ) +
  scale_x_continuous(limits = c(0, 45000), breaks = seq(0, 45000, 5000))
```

    Warning: Removed 2 rows containing missing values (`geom_bar()`).

![](KEY_Tutorial_2_files/figure-commonmark/adjust%20scales-1.png)

### 6.4: Clean Up

Alright, you have done a lot to improve the original histogram that
appeared! Let’s keep getting your visualization ready for prime time!

Removing clutter is often a wise choice when designing a visualization.
That is what you will do now.

#### 6.4: Tasks and Questions

1.  Copy and past the code from 6.3 into the gray space below.

2.  At the end of the line with `scale_x_continuous` put a `+`

3.  On the next line write in `theme_minimal()` and then run the entire
    chunk of code.

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram(binwidth = 2500)+
  labs(
    title ="What size loans to people get at Lending Club?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Loan Amount ($)",
    y = "Number of Loans"
  ) +
  scale_x_continuous(limits = c(0, 45000), breaks = seq(0, 45000, 5000)) +
  theme_minimal()
```

    Warning: Removed 2 rows containing missing values (`geom_bar()`).

![](KEY_Tutorial_2_files/figure-commonmark/clean%20up-1.png)

### 6.5: Fill the Bars and Add Color

#### 6.5: Tasks and Questions

1.  What are Lending Clubs 2 main corporate colors?

2.  Click [this
    link](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf) and
    find the names of the colors that best match Lending Clubs corporate
    colors. Copy one of the color names into the `""` that come after
    `fill =` . Copy the other color into the “” after color `=` .

``` r
loan50_small |>
  ggplot(aes(x = loan_amount)) +
  geom_histogram(binwidth = 2500, fill = "#002a4e", color = "#ef4123") +
  labs(
    title ="What size loans to people get at Lending Club?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Loan Amount ($)",
    y = "Number of Loans"
  ) +
  scale_x_continuous(limits = c(0, 45000), breaks = seq(0, 45000, 5000)) +
  theme_minimal()
```

    Warning: Removed 2 rows containing missing values (`geom_bar()`).

![](KEY_Tutorial_2_files/figure-commonmark/fill%20and%20color-1.png)

### 6.6: Put it all together.

You’ve done a lot so far. One by one, you adjusted various elements of
the histogram showing the loan amount data. Now you are going to work
with the **histogram you created in part 3.**

#### 6.6: Tasks and Questions

1.  Copy and paste the code you wrote for 3.2 into the gray space below
    and then run the code.

2.  Adjust the following elements of the histogram:

- labels.
- bin width
- axis scales
- theme
- fill and color

``` r
loan50_small |>
  ggplot(aes(x = total_income)) +
  geom_histogram(binwidth = 25000, fill = "#002a4e", color = "#ef4123") +
  labs(
    title ="What incomes do people who get loans from Lending Club tend to have?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Total Income ($)",
    y = "Number of Loans"
  ) +
  scale_x_continuous(limits = c(0, 400000), breaks = seq(0, 400000, 50000)) +
  theme_minimal()
```

    Warning: Removed 2 rows containing missing values (`geom_bar()`).

![](KEY_Tutorial_2_files/figure-commonmark/put%20it%20all%20together-1.png)

### 7 Bonus:

#### Bonus Tasks

1.  Turn the histogram you just made into a density curve.

2.  Add a vertical line that represents the median of the data being
    visualized. *(Hint: Bing Chat in creative mode is your friend)*

``` r
# Calculate the median value of total income
median_income <- median(loan50_small$total_income)

loan50_small |>
  ggplot(aes(x = total_income)) +
  geom_density(binwidth = 25000, fill = "#002a4e", color = "#ef4123") +
  labs(
    title ="What incomes do people who get loans from Lending Club tend to have?",
    subtitle = "Sample of 50 loans from Lending Club",
    x = "Total Income ($)",
    y = "Number of Loans"
  ) +
  scale_x_continuous(limits = c(0, 400000), breaks = seq(0, 400000, 50000)) +
  theme_minimal() +
  # Add median line with color and label
  geom_vline(aes(xintercept = median_income, color = "Median"), linetype = "dashed") +
  # Add text with median value next to the line
  annotate(
    "text",
    label = paste("Median: $", round(median_income, digits = 0)),
    x = median_income + 5000,
    y = 1.0e-5 / 2,
    color = "#ef4123",
    hjust = "left"
  )
```

    Warning in geom_density(binwidth = 25000, fill = "#002a4e", color = "#ef4123"):
    Ignoring unknown parameters: `binwidth`

![](KEY_Tutorial_2_files/figure-commonmark/bonus%20median%20line-1.png)

I used Bing in Creative mode to help generate this answer. Here is the
conversation:

Me:

How do I add a median line to the following visualization? I also want
to add text next to the line that gives the number of the median.
loan50_small \|\> ggplot(aes(x = total_income)) + geom_density(binwidth
= 25000, fill = “\#002a4e”, color = “\#ef4123”) + labs( title =“What
incomes do people who get loans from Lending Club tend to have?”,
subtitle = “Sample of 50 loans from Lending Club”, x = “Total Income
(\$)”, y = “Number of Loans” ) + scale_x_continuous(limits = c(0,
400000), breaks = seq(0, 400000, 50000)) + theme_minimal()

Bing:

To add a median line and a text label to your ggplot2 visualization, you
can use the following steps:

- Calculate the median value of the total income variable using the
  **`median`** function.

- Use **`geom_vline`** to add a vertical line at the median value. You
  can customize the color and linetype of the line using the **`aes`**
  argument.

- Use **`annotate`** to add a text annotation next to the line. You can
  use **`paste`** or **`glue`** to combine the text and the median
  value. You can also adjust the position and alignment of the text
  using the **`x`**, **`y`**, and **`hjust`** arguments.

Here is an example of how your code could look like:

**R**

    # Calculate the median value of total income
    median_income <- median(loan50_small$total_income)

    # Add median line and text label
    loan50_small %>%
      ggplot(aes(x = total_income)) +
      geom_density(binwidth = 25000, fill = "#002a4e", color = "#ef4123") +
      labs(
        title ="What incomes do people who get loans from Lending Club tend to have?",
        subtitle = "Sample of 50 loans from Lending Club",
        x = "Total Income ($)",
        y = "Number of Loans"
      ) +
      scale_x_continuous(limits = c(0, 400000), breaks = seq(0, 400000, 50000)) +
      theme_minimal() +
      # Add median line with color and label
      geom_vline(aes(xintercept = median_income, color = "Median"), linetype = "dashed") +
      # Add text with median value next to the line
      annotate(
        "text",
        label = paste("Median: $", round(median_income, digits = 0)),
        x = median_income + 5000,
        y = max(density) / 2,
        color = "black",
        hjust = "left"
      )

AI-generated code. Review and use carefully. [More info on
FAQ](https://www.bing.com/new#faq).

I hope this helps you with your visualization. 😊

Learn more

[1![](blob:https://www.bing.com/508adc8e-443a-404b-8364-f2719ef7d9fc.png)stackoverflow.com](https://stackoverflow.com/questions/53054916/r-displaying-mean-and-median-labels-on-boxplot-ggplot)[2![](blob:https://www.bing.com/0da22ddb-d85b-4bb6-9981-f70ff9f69868.png)sthda.com](http://www.sthda.com/english/wiki/ggplot2-texts-add-text-annotations-to-a-graph-in-r-software)[3![](blob:https://www.bing.com/508adc8e-443a-404b-8364-f2719ef7d9fc.png)stackoverflow.com](https://stackoverflow.com/questions/23412447/adding-vertical-lines-through-median-values-of-cumulative-distributions-ggplot2)
