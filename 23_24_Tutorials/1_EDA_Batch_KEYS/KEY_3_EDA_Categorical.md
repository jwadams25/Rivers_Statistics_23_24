# KEY Tutorial 3: EDA with Categorical Data
Mr. Adams

- [EDA with Categorical Data](#eda-with-categorical-data)
- [Libraries](#libraries)
- [1: Exploring One Categorical
  Variable](#exploring-one-categorical-variable)
  - [1.1 Data for Part One](#data-for-part-one)
    - [1.1: Tasks and Questions](#tasks-and-questions)
  - [1.2 Build a table](#build-a-table)
    - [1.2 Tasks and Questions](#tasks-and-questions-1)
  - [1.3 Table with Proportions and
    Counts](#table-with-proportions-and-counts)
    - [1.3 Tasks and Questions](#tasks-and-questions-2)
  - [1.4 Arranging the table](#arranging-the-table)
    - [1.4 Tasks and Questions](#tasks-and-questions-3)
  - [1.5: Build a Bar Graph](#build-a-bar-graph)
    - [1.5 Tasks and Questions](#tasks-and-questions-4)
  - [1.6: Adjust bar graph to implement some data visualizations best
    practices.](#adjust-bar-graph-to-implement-some-data-visualizations-best-practices.)
    - [1.6a: Horizontal Bars and Labels](#a-horizontal-bars-and-labels)
    - [1.6b: Arranging the bars and changing
      colors](#b-arranging-the-bars-and-changing-colors)
- [2: Exploring Two Categorical
  Variables](#exploring-two-categorical-variables)
  - [2.1: Contingency Table with Counts](#contingency-table-with-counts)
    - [2.1: Tasks and Questions](#tasks-and-questions-5)
  - [2.2: Contingency Table with
    Proportions.](#contingency-table-with-proportions.)
    - [2.2: Tasks and Questions](#tasks-and-questions-6)
  - [2.3: Visualize Two Categorical Variables with a Filled Bar
    Plot](#visualize-two-categorical-variables-with-a-filled-bar-plot)
    - [2.3a: Create a Filled Bar Graph](#a-create-a-filled-bar-graph)
    - [2.3b Adjust filled bar graph to include some data visualization
      best
      practices](#b-adjust-filled-bar-graph-to-include-some-data-visualization-best-practices)

# EDA with Categorical Data

# Libraries

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
library(janitor)
```


    Attaching package: 'janitor'

    The following objects are masked from 'package:stats':

        chisq.test, fisher.test

``` r
library(knitr)
library(kableExtra)
```


    Attaching package: 'kableExtra'

    The following object is masked from 'package:dplyr':

        group_rows

``` r
library(gridExtra)
```


    Attaching package: 'gridExtra'

    The following object is masked from 'package:dplyr':

        combine

``` r
library(readr)
```

# 1: Exploring One Categorical Variable

## 1.1 Data for Part One

To learn how you can explore one categorical variable using R, you will
use the data in the `openintro` packaged called `immigration`.

[Click here to read a description of the
dataset.](http://openintrostat.github.io/openintro/reference/immigration.html)

### 1.1: Tasks and Questions

1.  Without running the code below, read the code and write down what
    the name of the data frame will be. (Be sure to type the name
    EXACTLY as it appears in the code)

    `immigration`

2.  What are the observational units?

    "910 randomly sampled registered voters in Tampa, FL"

3.  How many observations are there? (You can now run the code to help
    answer this question.)

    910

4.  List the two variables included in this data frame. Be sure to list
    the name of the variable exactly as it appears and label the type of
    each variable.

    `political`

    `response`

``` r
# View it and take a glimpse of it.

view(immigration)

glimpse(immigration)
```

    Rows: 910
    Columns: 2
    $ response  <fct> Apply for citizenship, Apply for citizenship, Apply for citi…
    $ political <fct> conservative, conservative, conservative, conservative, cons…

## 1.2 Build a table

Now that you have an understanding of the data, let’s start exploring.

To begin, we will ask a question:

**How many of the survey respondents described themselves as having a
political ideology of either conservative, liberal, or moderate?**

Obviously, we are not going to look at the data and get our answer by
counting by hand! What a waste of time! One thing we could do is tell
the computer to build a table for us! The structure of the code required
to make a table will read like this:

Look at this data called immigration AND THEN count the number of items
for each level in this categorical variable.

### 1.2 Tasks and Questions

1.  Based on the description above that details the structure of the
    code, erase the `______` sections in the code chunk below and
    replace them with either the *name of the data set* or *the name of
    the variable* needed to answer our question.

2.  Which political ideology had the most respondents? How many did they
    have?

    372 respondents to this poll identified as having a conservative
    political ideology.

``` r
immigration |>
  count(political)
```

    # A tibble: 3 × 2
      political        n
      <fct>        <int>
    1 conservative   372
    2 liberal        175
    3 moderate       363

## 1.3 Table with Proportions and Counts

Knowing the total in each group is helpful. Knowing what proportion of
respondents fell into each level can also be helpful. To get that
information you have to add one line of code to what you wrote in part
1.2.

That line of code is what you see in the gray space below. The mutate
function in that line is creating a new variable called proportion that
takes the number of respondents in each level and divides each of those
by the total number of respondents.

### 1.3 Tasks and Questions

1.  Copy the code you wrote in part 1.2 into the line above the code you
    see below.

2.  Add the pipe symbol, `|>`, at the end of the line that has `count`.

3.  Run the code.

4.  What proportion of the respondents identified themselves as
    moderate?

    Respondents who identified themselves as moderates made up roughly
    39.9% of the entire sample.

5.  **(BONUS)** Add a new variable to this data frame that shows the
    percentage of respondents for each political ideology.

``` r
immigration |>
  count(political) |>
  mutate(proportion = n / sum(n)) 
```

    # A tibble: 3 × 3
      political        n proportion
      <fct>        <int>      <dbl>
    1 conservative   372      0.409
    2 liberal        175      0.192
    3 moderate       363      0.399

## 1.4 Arranging the table

We’ve talked a lot about clear and effective communication. One way to
do that when making a table is by arranging the table in a meaningful
way. The political ideology variable is not ordinal so we can order the
table from least to greatest or greatest to least. Again, adding one
line of code to what we’ve already created will do just that.

### 1.4 Tasks and Questions

1.  Copy the code from part 1.3 and paste it into the gray space below.

2.  Add a pipe symbol, `|>`, after the row that includes mutate.

3.  In the next line of code add: `arrange(desc(proportion))`

4.  Run the entire code chunk.

5.  What do you think `desc`, which is in the line of code your wrote,
    stands for?

``` r
immigration |>
  count(political) |>
  mutate(proportion = n / sum(n)) |>
  arrange(desc(proportion))
```

    # A tibble: 3 × 3
      political        n proportion
      <fct>        <int>      <dbl>
    1 conservative   372      0.409
    2 moderate       363      0.399
    3 liberal        175      0.192

## 1.5: Build a Bar Graph

After building the table, you now have a better understanding of the
respondents to the survey. The table could be used as a visualization.
However, often times people can more easily and quickly see the major
takeaways from a bar graph. The table would then provide you with the
numbers to support what is displayed in the bar graph.

We will now build a bar graph that shows what is in the table you just
created. The structure of the code to do this will look very similar to
the code you wrote to make histograms and density curves in the previous
tutorial.

To answer this question…

- I need this data frame and then

- I specifically want to make a plot with this variable and need to put
  it on the blank axis and

- create this visualization.

### 1.5 Tasks and Questions

1.  Change `NAME_OF_DATA_FRAME` and `CATEGORICAL_VARIABLE` so you create
    a bar graph that visualizes the same information you created in 1.2.

2.  Run the code.

3.  What are three design changes you’d like to make to this
    visualization to make it easier for someone to read?

    Order the bars from greatest to least.

    Add a title and subtitle.

    Improve the labels on each axis.

    Make the bars extend horizontally instead of vertically.

``` r
immigration |>
  ggplot(aes(x = political)) +
  geom_bar()
```

![](KEY_3_EDA_Categorical_files/figure-commonmark/bar%20graph-1.png)

## 1.6: Adjust bar graph to implement some data visualizations best practices.

Making a bar graph without adjusting any design elements should be your
**first step** when exploring data. **Keep it simple** and keep your
process short as you start learning about the data.

Only after that can you begin to say things like, “Oh, given what it
shows, I should change the title to \_\_\_, the scales on the axes need
adjusting, and flip it horizontally.”

This next section of this tutorial will guide you through adding or
adjusting layers of code to produce a more polished bar graph.

These are the steps you are taking as you prepare to put your
visualizations into a paper or presentation.

### 1.6a: Horizontal Bars and Labels

Let’s begin by making the bars lay horizontally and adding in a few of
the design layers you learned in the second tutorial.

#### 1.6a: Tasks and Questions

1.  The code chunk below will cause the bars to lay horizontally. It
    looks VERY similar to the code written in 1.5. What was changed in
    the code from 1.5 to make the bars lay horizontally?

2.  Add in appropriate labels in between each `""`.

``` r
immigration |>
  ggplot(aes(y = political)) +
  geom_bar() +
  labs(x = "Number of People", 
       y = "", 
       title = "Political Ideologies of Registered Voters in Tampa, Florida", 
       subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida") 
```

![](KEY_3_EDA_Categorical_files/figure-commonmark/horizontal%20and%20labels-1.png)

### 1.6b: Arranging the bars and changing colors

You will also want to help an observer of your visualization by ordering
the bars from greatest to least, filling the bars in with meaningful
colors, and removing some clutter.

The changes to what comes after `y =` in the code below change the order
of the bars from least to greatest.

Putting political after `fill =` is a necessary step given how you will
adjust the color of the bars.

#### 1.6b: Tasks and Questions

1.  Given the context of what we are visualizing, what colors would best
    fit each bar? Again, feel free to reference [this site for the names
    of the colors you
    want](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf).

2.  Change `CONSERVATIVE_COLOR`, `LIBERAL_COLOR`, and `MODERATE_COLOR`
    in the code below to the names of the colors you selected in
    question 1. Keep the quotes around each color name.

3.  Run the code and pat yourself on the back!

``` r
immigration |>  
  ggplot(aes(y = fct_rev(fct_infreq(political)), fill = political)) +
  geom_bar() +
  labs(x = "Number of People", 
       y = "", 
       title = "Political Affiliations of Registered Votes in Tampa, Florida", 
       subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida") +
  scale_fill_manual(values = c("red3","blue4", "slategray"), guide = FALSE) +
  theme_minimal()
```

    Warning: The `guide` argument in `scale_*()` cannot be `FALSE`. This was deprecated in
    ggplot2 3.3.4.
    ℹ Please use "none" instead.

![](KEY_3_EDA_Categorical_files/figure-commonmark/complete%20bar-1.png)

# 2: Exploring Two Categorical Variables

The question you answered on one of your homework assignments was, “Do
political ideology and views on immigration appear to be associated?”

Answering that question requires you to explore two categorical
variables. This part of the tutorial will walk you through building
contingency tables and filled bar plots.

## 2.1: Contingency Table with Counts

Let’s start by recreating the table you saw on this homework problem. To
get a refresher, [visit question 2 by clicking
here.](https://openintro-ims.netlify.app/explore-categorical.html#chp4-exercises)

### 2.1: Tasks and Questions

1.  Change `NAME_OF_DATA_FRAME` and `SECOND_VARIABLE` so you can create
    the contingency table with the right information.

2.  Given the results in the table and bar graph you produced in part 1
    of this tutorial, why might we not want to compare the NUMBER of
    people within each political ideology that responded for each level
    of immigration?

    Given the size of each group varies, comparing the numbers of
    responses may lead us to incorrect conclusions.

``` r
immigration |>
  count(political, response) |>
  pivot_wider(names_from = political, values_from = n) |>
  adorn_totals(where = c("row", "col"))
```

                  response conservative liberal moderate Total
     Apply for citizenship           57     101      120   278
              Guest worker          121      28      113   262
         Leave the country          179      45      126   350
                  Not sure           15       1        4    20
                     Total          372     175      363   910

## 2.2: Contingency Table with Proportions.

In the code below, you will create a contingency with column
proportions.

In other words, you want to have a table that can help answer questions
like, “What **proportion** OF THOSE who are conservative responded by
saying they support applying for citizenship?”

### 2.2: Tasks and Questions

1.  Change `NAME_OF_DATA_FRAME`, `FIRST_VARIABLE`, and `SECOND_VARIABLE`
    in the code below to create the contingency table described above.

``` r
 immigration|>
  count(political, response) |> 
  group_by(political) |>
  mutate(proportion = n / sum(n)) |> 
  select(-n) |>
  pivot_wider(names_from = political, values_from = proportion)
```

    # A tibble: 4 × 4
      response              conservative liberal moderate
      <fct>                        <dbl>   <dbl>    <dbl>
    1 Apply for citizenship       0.153  0.577     0.331 
    2 Guest worker                0.325  0.16      0.311 
    3 Leave the country           0.481  0.257     0.347 
    4 Not sure                    0.0403 0.00571   0.0110

## 2.3: Visualize Two Categorical Variables with a Filled Bar Plot

As we did in part one, we want to create a data visualization in
addition to a table. Because there was a big difference between the
number of people who responded from each political ideology, we will
make a filled bar plot.

### 2.3a: Create a Filled Bar Graph

#### 2.3a: Tasks and Questions

1.  Before we dive into the code, take out either a piece of paper or
    your iPad and draw a rough sketch of the filled bar plot that will
    support the table you created in part 2.2. We are going to make the
    bars lay horizontally. You do not have to draw it to exact scale.
    Instead be sure you can identify what variable will be on the
    y-axis, what variable you will fill the bars, and what labels will
    you want to include.

Call Mr. Adams over before going to the next step.

2.  Change `NAME_OF_DATA_FRAME`, `FIRST_VARIABLE`, and `SECOND_VARIABLE`
    in the code below to create the filled bar graph you made in
    question

3.  Add in a title, labels for each axis, and a label for the key.

4.  Run the code and pat yourself on the back!

``` r
immigration |>
  ggplot(aes(y = political, fill = response)) +
  geom_bar(position = "fill", color = "white") +
  labs(
    title = "What should workers who have entered the country \nillegally be allowed to or have to do?",
    subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida",
    x = "Proportion",
    y = "Political Ideology",
    fill = ""
  )
```

![](KEY_3_EDA_Categorical_files/figure-commonmark/standardized%20bar-1.png)

### 2.3b Adjust filled bar graph to include some data visualization best practices

Like before, we want the main takeaway to pop out to the viewer of this
visualization. In this case we will highlight the filled spaces
representing proportion supporting Apply for Citizenship and order the
bars from least to greatest proportion that support Apply for
Citizenship.

#### 2.3b Tasks and Questions

1.  In the row that starts with `scale_fill_manual`, change the
    `APPLY's color` to any color you’d like. Change all the other colors
    to `lightgray` (NO SPACES in lightgray)

2.  Run the code and pat yourself on the back!

3.  Now that you’ve seen the visualization, add in a subtitle that will
    highlight the major takeaway from this visualization.

4.  Run the code again. Stand up. Put your hands in the air and yell,
    “LET’S GOOOOO!!!”

5.  After your brief celebration, write answer the question we started
    with in this part of the tutorial: “Do political ideology and views
    on immigration appear to be associated?”

``` r
immigration |>
  ggplot(aes(y = fct_rev(fct_infreq(political)), fill = response)) +
  geom_bar(position = "fill", color = "white") +
  labs(
    title = "What should workers who have entered the country \nillegally be allowed to or have to do?",
    subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida",
    x = "Proportion",
    y = "Political Ideology",
    fill = ""
  ) +
  scale_fill_manual(values = c("red", "lightgray", "lightgray","lightgray")) +
  theme_minimal()
```

![](KEY_3_EDA_Categorical_files/figure-commonmark/final-1.png)
