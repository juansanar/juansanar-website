---
title: "Got 528 tab problems"
description: "...but defeat ain't one."
date: 2022-04-05
author: "Juan C. Sanchez-Arias"
tags: ["PKM", "R", "Data Science"]
---

![Open tabs preview](/blog-img/2022-03-28-22-28-54.png)

> How many times have you said to yourself: *"I'll leave this X number of tabs open for now and will check them later to complete (insert task)?"*

The revolutionary introduction of tabs to browsers initiated by "InternetWorks" (developed by BookLink Technologies) and popularized by Mozilla Firefox has allowed users to open as many tabs as they want within a single browser window, limited only by the user's RAM and tolerability to unreadable (and often unclickable) tabs on the browser title bar. This, combined with the increasingly available RAM in modern computers, can quickly create a disaster of open tabs if one doesn't pay attention.

As shown in the image above, I fell into the bottomless pit of multiple browsers, with multiple tabs across multiple desktop instances. The result: **528 open tabs**. Yes, 528 tabs. Open. All the time. Using Google Chrome.

![Chrome memory usage meme](https://tl360.b-cdn.net/wp-content/uploads/2016/11/Simple-Hacks-And-Best-Tools-To-Limit-Memory-Usage-In-Google-Chrome-1200x720.jpg)

### What is the reason underlying this chaos?

Such chaos is simply the result of **disorganization**. More specifically, **disorganized thoughts and ideas**. These 528 tabs represent 528 thoughts and ideas that were not written down, categorized, and interconnected in a timely and structured fashion.

In other words, I was using multiple tabs as a makeshift personal knowledge management (PKM) system—and it was an awful idea.

> **What is Personal Knowledge Management (PKM)?**  
> A process of collecting information in a structured manner so it is retrievable, shareable, and scalable. In simpler terms: a system that can be used as your *second brain*.

### Analyzing My Open Tabs with R and TidyText

It is #TidyTuesday after all, so let's explore what were the most common words present in those open tabs using `tidytext` and `wordcloud` in R!

```r
library(readr)
library(dplyr)
library(tidyr)
library(stringr)
library(tidytext)
library(wordcloud)

# Tidying tab titles and tokenizing words
text_df <- tibble(line = 1:371, text = tabs_df$url_title)

text_unnested <- text_df %>% unnest_tokens(word, text)

text_filtered <- text_unnested %>% 
  filter(!word %in% c("the", "and", "of", "in", "a", "to", "for", "at", "is", "are", "as", "on", "by", "it", "its")) %>% 
  count(word, sort = TRUE)

# Generate wordcloud
wordcloud(
  words = text_filtered$word,
  freq = text_filtered$n, 
  min.freq = 1, max.words = 200, 
  random.order = FALSE, rot.per = 0.35, 
  colors = rev(viridis::magma(n = 100))
)
```

![Wordcloud of 528 tabs](/blog-img/wordcloud-1.png)
