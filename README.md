# How-I-Met-Your-Mother-Analysis
Text mining from the How I Met Your Mother (Tv-series) transcripts and finding trends like ’Most pivotal character’, ’Relation - Graph among characters’ and ’Analysis of catch phrases used by Barney Stinson’

# Problem Statement
How I met Your Mother(HIMYM) has turned out to be the most watched Comedy-Drama Sitcom in the world (trailed by Friends). Thus analysing and visualising the transcripts of HIMYM would be a really interesting and fun activity. All the coding was done using R and some great R packages. After following and watching, tens of web-series and sitcoms, HIMYM has landed in the top-charts of my favourites list. Thus, analysing the scripts and getting some results would be very interesting and fun activity for a die-hard fan of the sitcom, like me. Also, I had the opportunity to perform web-scrapping, analysing patterns and data-storytelling using R, which was a great motivation to create this project. It was really challenging to use efficiently the functions in the tidyverse, tidytext and shiny dashboard packages. There is an opportunity to generalise this combined method  to analyse any given Sitcom. This could provide a platform even for new upcoming Sitcoms to predict the popularity of a character just by analysing the transcripts of the Sitcom, which might help the casting directors to cast a character efficiently .

# Data Source
HIMYM, we know there’s around nine seasons, each one with about 22 episodes. This makes about 200 episodes give or take. It would be a big pain to manually write down 200 complicated URL’s. Luckily, there is a way of finding the 200 links without writing them down manually.

# Research Questions
I formulated three research questions for this project. The questions are as mentioned below:
1. Analysis of catchphrases used by Barney Stinson (a main-character in the series), based on each season. A bar-graph is proposed for this story, which can be used to show the count of each catchphrase being used over ever season
2. Which characters had the best on-screen chemistry i.e. how strongly they are related to each other? This will be done by analysing which character was mentioned in another characters dialogue. A linear arc graph is proposed for this story.
3. Which character was most significant in the whole series or in each season? This will be done by calculating the total number of words/lines each character had in each episode, which will then be cumulated for every season. A frequency plot is proposed for visualising this story

These stories then has to be displayed in a dashboard, in a single page or in multiple pages. The package shinydashboard will be used for this purpose.

# Architecture
First the links containing all 9 seasons was created, then create a tibble containing all episodes with its individual links and the episode name. Then a function was created which turns the html text into a data frame and organizes it clearly for text analysis. This function was applied to all the episodes, which gives us a tibble containing the actual transcript for each episode (which has dialogues and the character who spoke it, separated by “:”). Now, we break down each script into lines, and assign it to the character who has spoken it; this was again stored in a tibble. This lines_per_character tibble was then used to check, for characters which had its named mentioned in another character’s dialogue. This data was obtained was obtained in a vector, which was then used to plot an edge-graph to show the relationship between characters. Again, we use the lines_per_character and filter out all Barney’s lines to find the occurrences of catchphrases in his dialogues. After some research, only the top 10 catchphrases were found (from fan-blogs) and considered for this project. A text-search was performed over all the lines, to fetch the number of times each catchphrase was spoken in a particular episode, which was then cumulated per season and was plotted. Also, the top 3 catchphrase in each season was stored in a table. Further the lines_per_character tibble was drilled down to get words_per_character, which was used to plot frequency graphs showing the importance of each character by visualising the presence of each character in terms of words over time. Also, an area plot was created which showed the percentage of words each character had per season. Then, using the shiny and shinydashboard packages, a web-based dashboard was created. Using different features of these packages, the above mentioned graphs/plots were arranged and displayed beautifully and in an organised way in the dashboard.

