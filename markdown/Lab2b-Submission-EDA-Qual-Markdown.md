---
editor_options: 
  markdown: 
    wrap: 72
---

# Student Details

+---------------+----------------------------------------------------+
| **Student ID  | 1.  136895 - C - Wesley Wanyama                    |
| Numbers and   |                                                    |
| Names of      | 2.  136446 - C - Mirav Bhojani                     |
| Group         |                                                    |
| Members**     | 3.  136788 - C - Derrick Nyaga                     |
|               |                                                    |
|               | 4.  136709 - C - Jane Mugo                         |
|               |                                                    |
|               | 5.  135399 - C - Sheilla Kavinya                   |
+---------------+----------------------------------------------------+
| **GitHub      | *Team Marafiki*                                    |
| Classroom     |                                                    |
| Group Name**  |                                                    |
+---------------+----------------------------------------------------+
| **Course      | BBT4206                                            |
| Code**        |                                                    |
+---------------+----------------------------------------------------+
| **Course      | Business Intelligence II                           |
| Name**        |                                                    |
+---------------+----------------------------------------------------+
| **Program**   | Bachelor of Business Information Technology        |
+---------------+----------------------------------------------------+
| **Semester    | 21^st^ August 2023 to 28^th^ November 2023         |
| Duration**    |                                                    |
+---------------+----------------------------------------------------+

# Setup Chunk

We start by installing all the required packages

\`\`\`{r Install Packages, echo=TRUE, message=FALSE, warning=FALSE} \##
formatR - Required to format R code in the markdown ---- if
(!is.element("formatR", installed.packages()$$, 1$$)) {
install.packages("formatR", dependencies = TRUE,
repos="<https://cloud.r-project.org>") } require("formatR")

## readr - Load datasets from CSV files ----

if (!is.element("readr", installed.packages()$$, 1$$)) {
install.packages("readr", dependencies = TRUE,
repos="<https://cloud.r-project.org>") } require("readr")

if (!is.element("dplyr", installed.packages()$$, 1$$)) {
install.packages("dplyr", dependencies = TRUE, repos =
"<https://cloud.r-project.org>") } require("dplyr")

## ggplot2 - For data visualizations using the Grammar for Graphics package ----

if (!is.element("ggplot2", installed.packages()$$, 1$$)) {
install.packages("ggplot2", dependencies = TRUE, repos =
"<https://cloud.r-project.org>") } require("ggplot2")

library(dplyr)

```         
------------------------------------------------------------------------

**Note:** the following "*KnitR*" options have been set as the defaults in this markdown:\
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE, collapse = FALSE, tidy.opts = list(width.cutoff = 80), tidy = TRUE)`.

More KnitR options are documented here <https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and here <https://yihui.org/knitr/options/>.

```{r setup, echo=TRUE, message=FALSE, warning=FALSE}
knitr::opts_chunk$set(
    eval = TRUE,
    echo = TRUE,
    warning = FALSE,
    collapse = FALSE,
    tidy = TRUE
)
```

------------------------------------------------------------------------

**Note:** the following "*R Markdown*" options have been set as the
defaults in this markdown:

> output:\
> \
> github_document:\
> toc: yes\
> toc_depth: 4\
> fig_width: 6\
> fig_height: 4\
> df_print: default\
> \
> editor_options:\
> chunk_output_type: console

# Loading the Student Performance Dataset

The 20230412-20230719-BI1-BBIT4-1-StudentPerformanceDataset is then
loaded. The dataset and its metadata are available here:
<https://drive.google.com/drive/folders/1-BGEhfOwquXF6KKXwcvrx7WuZXuqmW9q?usp=sharing>

`` {r Load Dataset} student_performance_dataset <-   readr::read_csv(                   "../data/20230412-20230719-BI1-BBIT4-1-StudentPerformanceDataset.CSV", # nolint                   col_types =                   readr::cols(                               class_group =                               readr::col_factor(levels = c("A", "B", "C")),                               gender = readr::col_factor(levels = c("1", "0")),                               YOB = readr::col_date(format = "%Y"),                               regret_choosing_bi =                               readr::col_factor(levels = c("1", "0")),                               drop_bi_now =                               readr::col_factor(levels = c("1", "0")),                               motivator =                               readr::col_factor(levels = c("1", "0")),                               read_content_before_lecture =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               anticipate_test_questions =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               answer_rhetorical_questions =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               find_terms_I_do_not_know =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               copy_new_terms_in_reading_notebook =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               take_quizzes_and_use_results =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               reorganise_course_outline =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               write_down_important_points =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               space_out_revision =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               studying_in_study_group =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               schedule_appointments =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               goal_oriented =                               readr::col_factor(levels =                                                 c("1", "0")),                               spaced_repetition =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               testing_and_active_recall =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               interleaving =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               categorizing =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               retrospective_timetable =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               cornell_notes =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4")),                               sq3r = readr::col_factor(levels =                                                        c("1", "2", "3", "4")),                               commute = readr::col_factor(levels =                                                           c("1", "2",                                                             "3", "4")),                               study_time = readr::col_factor(levels =                                                              c("1", "2",                                                                "3", "4")),                               repeats_since_Y1 = readr::col_integer(),                               paid_tuition = readr::col_factor(levels =                                                                c("0", "1")),                               free_tuition = readr::col_factor(levels =                                                                c("0", "1")),                               extra_curricular = readr::col_factor(levels =                                                                    c("0", "1")),                               sports_extra_curricular =                               readr::col_factor(levels = c("0", "1")),                               exercise_per_week = readr::col_factor(levels =                                                                     c("0", "1",                                                                       "2",                                                                       "3")),                               meditate = readr::col_factor(levels =                                                            c("0", "1",                                                              "2", "3")),                               pray = readr::col_factor(levels =                                                        c("0", "1",                                                          "2", "3")),                               internet = readr::col_factor(levels =                                                            c("0", "1")),                               laptop = readr::col_factor(levels = c("0", "1")),                               family_relationships =                               readr::col_factor(levels =                                                 c("1", "2", "3", "4", "5")),                               friendships = readr::col_factor(levels =                                                               c("1", "2", "3",                                                                 "4", "5")),                               romantic_relationships =                               readr::col_factor(levels =                                                 c("0", "1", "2", "3", "4")),                               spiritual_wellnes =                               readr::col_factor(levels = c("1", "2", "3",                                                            "4", "5")),                               financial_wellness =                               readr::col_factor(levels = c("1", "2", "3",                                                            "4", "5")),                               health = readr::col_factor(levels = c("1", "2",                                                                     "3", "4",                                                                     "5")),                               day_out = readr::col_factor(levels = c("0", "1",                                                                      "2", "3")),                               night_out = readr::col_factor(levels = c("0",                                                                        "1", "2",                                                                        "3")),                               alcohol_or_narcotics =                               readr::col_factor(levels = c("0", "1", "2", "3")),                               mentor = readr::col_factor(levels = c("0", "1")),                               mentor_meetings = readr::col_factor(levels =                                                                   c("0", "1",                                                                     "2", "3")),                               `Attendance Waiver Granted: 1 = Yes, 0 = No` =                               readr::col_factor(levels = c("0", "1")),                               GRADE = readr::col_factor(levels =                                                         c("A", "B", "C", "D",                                                           "E"))),                   locale = readr::locale()) ``

## Description of the Dataset

We then display the number of observations and number of variables. We
have 101 observations and 100 variables to work with.

`{r Your Fourth Code Chunk} dim(student_performance_dataset)`

Next, we display the quartiles for each numeric variable

`{r Your Fifth Code Chunk} summary(student_performance_dataset)`

## Custom theme for visualization

\`\`\`{r Visualization theme} blue_grey_theme \<- function() { theme(
axis.ticks = element_line( linewidth = 1, linetype = "dashed", lineend =
NULL, color = "#dfdede", arrow = NULL, inherit.blank = FALSE), axis.text
= element_text( face = "bold", color = "#3f3f41", size = 12, hjust =
0.5), axis.title = element_text(face = "bold", color = "#3f3f41", size =
14, hjust = 0.5), plot.title = element_text(face = "bold", color =
"#3f3f41", size = 16, hjust = 0.5), panel.grid = element_line( linewidth
= 0.1, linetype = "dashed", lineend = NULL, color = "#dfdede", arrow =
NULL, inherit.blank = FALSE), panel.background = element_rect(fill =
"#f3eeee"), legend.title = element_text(face = "plain", color =
"#3f3f41", size = 12, hjust = 0), legend.position = "right" ) }

```         
## Customize the text tables for consistency using HTML formatting

```{r Your sixth Code Chunk}
kable_theme <- function(dat, caption) {
  kable(dat, "html", escape = FALSE, caption = caption) %>%
    kable_styling(bootstrap_options = c("striped", "condensed", "bordered"),
                  full_width = FALSE)
}
```

# Bar chart for the average evaluation rating for each class group per gender

Each bar indicates the average rating for a certain class group, and the
bars are divided into male and female categories. Each bar's height
corresponds to the average evaluation rating, allowing for easy
comparison of ratings between class groups and genders.

\`\``{r Average rating for each class group per gender} evaluation_per_group_per_gender <- student_performance_dataset %>%    mutate(`Student's
Gender`=            ifelse(gender == 1, "Male", "Female")) %>%   select(class_group, gender,`Student's
Gender`,`Average Course Evaluation Rating`) %>%   filter(!is.na(`Average
Course Evaluation Rating`)) %>%   group_by(class_group,`Student's
Gender`) %>%   summarise(average_evaluation_rating =               mean(`Average
Course Evaluation Rating\`)) %\>%
arrange(desc(average_evaluation_rating), .by_group = TRUE)

evaluation_per_group_per_gender %\>% rename(`Class Group` = class_group)
%\>% rename(`Average Course Evaluation Rating` =
average_evaluation_rating) %\>% select(`Class Group`,
`Student's Gender`, `Average Course Evaluation Rating`) %\>%
mutate(`Average Course Evaluation Rating` = color_tile("#B9BCC2",
"#536CB5") (`Average Course Evaluation Rating`)) %\>% kable("html",
escape = FALSE, align = "c", caption = "Course Evaluation Rating per
Group and per Gender") %\>% kable_styling(bootstrap_options =
c("striped", "condensed", "bordered"), full_width = FALSE)

evaluation_per_group_per_gender %\>% ggplot() + geom_bar(aes(x =
class_group, y = average_evaluation_rating, fill = `Student's Gender`),
stat = "identity", position = "dodge") + expand_limits(y = 0) +
blue_grey_theme() + scale_fill_manual(values = blue_grey_colours_2) +
ggtitle("Course Evaluation Rating per Group and per Gender") + labs(x =
"Class Group", y = "Average Rating")

```         
## Number of Significant Words in Evaluation Likes per Gender

The provided code generates a table-style visualization emphasizing the number of significant words in evaluation likes per gender. It uses the kable function from the knitr package. The data has been preprocessed by removing contractions, special characters, stopwords, short words, and censored words. To enhance the visual presentation of the table, styling options have been applied using bootstrap. These options include striping for improved readability, condensed layout for a more compact view, and borders for a clear distinction between rows and columns.

```{r Significant words in evaluation likes per gender}
word_count_per_gender_likes %>%
  mutate(num_words = color_bar("lightblue")(num_words)) %>%
  rename(`Number of Words` = num_words) %>%
  kable("html", escape = FALSE, align = "c",
        caption = "Number of Significant Words in Evaluation Likes 
                   per Gender: Minus contractions, special characters, 
                   stopwords, short words, and censored words.") %>%
  kable_styling(bootstrap_options =
                  c("striped", "condensed", "bordered"),
                full_width = FALSE)
```

## Number of Significant Words in Evaluation Likes per Group

The provided code generates a table-style visualization emphasizing the
number of significant words in evaluation likes per group. It uses the
kable function from the knitr package. The data has been preprocessed by
removing contractions, special characters, stopwords, short words, and
censored words. To enhance the visual presentation of the table, styling
options have been applied using bootstrap. These options include
striping for improved readability, condensed layout for a more compact
view, and borders for a clear distinction between rows and columns.

`` {r Significant words in evaluation likes per group} word_count_per_group %>%   mutate(num_words = color_bar("lightblue")(num_words)) %>%   rename(`Number of Words` = num_words) %>%   kable("html", escape = FALSE, align = "c",         caption = "Number of Significant Words in Evaluation Likes                     per Group: Minus contractions, special characters,                     stopwords, short words, and censored words.") %>%   kable_styling(bootstrap_options =                   c("striped", "condensed", "bordered"),                 full_width = FALSE) ``

## Number of Significant Words in Evaluation Wishes per Gender

The provided code generates a table-style visualization emphasizing the
number of significant words in evaluation wishes per gender. It uses the
kable function from the knitr package. The data has been preprocessed by
removing contractions, special characters, stopwords, short words, and
censored words. To enhance the visual presentation of the table, styling
options have been applied using bootstrap. These options include
striping for improved readability, condensed layout for a more compact
view, and borders for a clear distinction between rows and columns.

\`\``{r Significant words in evaluation wishes per gender} word_count_per_gender_wishes %>%   mutate(num_words = color_bar("lightblue")(num_words)) %>%   rename(`Number
of Words\` = num_words) %\>% kable("html", escape = FALSE, align = "c",
caption = "Number of Significant Words in Evaluation Wishes per Gender:
Minus contractions, special characters, stopwords, short words, and
censored words.") %\>% kable_styling(bootstrap_options = c("striped",
"condensed", "bordered"), full_width = FALSE)

```         
## Number of Significant Words in Evaluation Wishes per Group

The provided code generates a table-style visualization emphasizing the number of significant words in evaluation wishes per group. It uses the kable function from the knitr package. The data has been preprocessed by removing contractions, special characters, stopwords, short words, and censored words. To enhance the visual presentation of the table, styling options have been applied using bootstrap. These options include striping for improved readability, condensed layout for a more compact view, and borders for a clear distinction between rows and columns.

```{r Significant words in evaluation wishes per group}
word_count_per_group_wishes %>%
  mutate(num_words = color_bar("lightblue")(num_words)) %>%
  rename(`Number of Words` = num_words) %>%
  kable("html", escape = FALSE, align = "c",
        caption = "Number of Significant Words in Evaluation Wishes 
                   per Group: Minus contractions, special characters, 
                   stopwords, short words, and censored words.") %>%
  kable_styling(bootstrap_options =
                  c("striped", "condensed", "bordered"),
                full_width = FALSE)
```

## Most Frequently Used Words in Course Evaluation Likes for Female Students

This visualization focuses on the most frequently used words in course
evaluation likes for female students. The visualization uses a
horizontal bar plot where the x-axis represents the words (Likes), and
the y-axis represents the frequency of each word being used. The length
of each bar corresponds to the frequency of the respective word

`` {r Frequently used words in course evaluation likes for female students} evaluation_likes_filtered %>%   select(`Class Group`, `Student's Gender`,          `Average Course Evaluation Rating`, `Likes (tokenized)`) %>%   filter(`Student's Gender` == "Female") %>%   count(`Likes (tokenized)`, sort = TRUE) %>%   top_n(9) %>%   mutate(`Likes (tokenized)` = reorder(`Likes (tokenized)`, n)) %>%   ggplot() +   geom_col(aes(`Likes (tokenized)`, n), fill = blue_grey_colours_1) +   blue_grey_theme() +   xlab("Word in Course Evaluation") +   ylab("Number of Times Used (Term Frequency)") +   ggtitle("Most Frequently Used Words in Course Evaluation Likes for Female           Students") +   coord_flip() ``

## Most Frequently Used Words in Course Evaluation Likes for Male Students

This visualization focuses on the most frequently used words in course
evaluation likes for male students. The visualization uses a horizontal
bar plot where the x-axis represents the words (Likes), and the y-axis
represents the frequency of each word being used. The length of each bar
corresponds to the frequency of the respective word

`` {r Frequently used words in course evaluation likes for male students} evaluation_likes_filtered %>%   select(`Class Group`, `Student's Gender`,          `Average Course Evaluation Rating`, `Likes (tokenized)`) %>%   filter(`Student's Gender` == "Male") %>%   count(`Likes (tokenized)`, sort = TRUE) %>%   top_n(9) %>%   mutate(`Likes (tokenized)` = reorder(`Likes (tokenized)`, n)) %>%   ggplot() +   geom_col(aes(`Likes (tokenized)`, n), fill = blue_grey_colours_1) +   blue_grey_theme() +   xlab("Word in Course Evaluation") +   ylab("Number of Times Used (Term Frequency)") +   ggtitle("Most Frequently Used Words in Course Evaluation Likes for Male           Students") +   coord_flip() ``

## Most Frequently Used Words in Course Evaluation Likes for per Gender

This visualization is centered around the most frequently used words in
course evaluation likes, categorized by gender. It employs a bar plot to
represent the term frequency of each word. The x-axis represents the
words (Likes), the y-axis represents the number of times each word was
used, and the bars' length corresponds to the frequency of each
respective word.

`` {r Frequently used words in course evaluation likes per gender} popular_words %>%   ggplot(aes(row, n, fill = `Student's Gender`)) +   geom_col(fill = blue_grey_colours_1) +   blue_grey_theme() +   labs(x = "Word in Course Evaluation",        y = "Number of Times Used (Term Frequency)") +   ggtitle("Most Frequently Used Words in Course Evaluation Likes per Gender") +   facet_wrap(~`Student's Gender`, scales = "free") +   scale_x_continuous(                      breaks = popular_words$row,                      labels = popular_words$`Likes (tokenized)`) +   coord_flip() ``

## Most Frequently Used Words in Course Evaluation Wishes per class group

This visualization focuses on the most frequently used words in course
evaluation wishes, categorized by class group. The plot is a horizontal
bar chart that represents the term frequency of each word.

`` {r Most frequently used words in course evaluation wishes per class group} popular_words %>%   ggplot(aes(row, n, fill = `Class Group`)) +   geom_col(fill = blue_grey_colours_1) +   blue_grey_theme() +   labs(x = "Word in Course Evaluation",        y = "Number of Times Used (Term Frequency)") +   ggtitle("Most Frequently Used Words in Course Evaluation Wishes per            Class Group") +   facet_wrap(~`Class Group`, scales = "free") +   scale_x_continuous(                      breaks = popular_words$row,                      labels = popular_words$`Wishes (tokenized)`) +   coord_flip() ``

## Most Important Words by TF-IDF Score in Course Evaluation Likes by Gender

This visualization focuses on the most important words in course
evaluation likes, calculated using TF-IDF (Term Frequency-Inverse
Document Frequency), categorized by student gender. The plot is a
horizontal bar chart that represents the TF-IDF score for each word.

`` {r Most Important Words by TF-IDF score in course evaluation likes by gender} top_popular_tfidf_words %>%   ggplot(aes(x = row, tf_idf, fill = `Student's Gender`)) +   geom_col(fill = blue_grey_colours_1) +   blue_grey_theme() +   labs(x = "Word in Course Evaluation", y = "TF-IDF Score") +   ggtitle("Important Words using TF-IDF by Chart Level") +   ggtitle("Most Important Words by TF-IDF Score in Course Evaluation Likes per        Class Group") +   facet_wrap(~`Student's Gender`, scales = "free") +   scale_x_continuous(                      breaks = top_popular_tfidf_words$row,                      labels = top_popular_tfidf_words$`Likes (tokenized)`) +   coord_flip() ``

## Most Important Words by TF-IDF Score in Course Evaluation Likes per Class Group

This visualization focuses on the most important words in course
evaluation likes, calculated using TF-IDF (Term Frequency-Inverse
Document Frequency), categorized per class group. The plot is a
horizontal bar chart that represents the TF-IDF score for each word.

`` {r Most important words by TF-IDF Score in Course Evaluation Likes per Class Group} top_popular_tfidf_words %>%   ggplot(aes(x = row, tf_idf, fill = `Class Group`)) +   geom_col(fill = blue_grey_colours_1) +   blue_grey_theme() +   labs(x = "Word in Course Evaluation", y = "TF-IDF Score") +   ggtitle("Important Words using TF-IDF by Chart Level") +   ggtitle("Most Important Words by TF-IDF Score in Course Evaluation Likes per        Class Group") +   facet_wrap(~`Class Group`, scales = "free") +   scale_x_continuous(                      breaks = top_popular_tfidf_words$row,                      labels = top_popular_tfidf_words$`Likes (tokenized)`) +   coord_flip() ``
