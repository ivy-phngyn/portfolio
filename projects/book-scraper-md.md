---
layout: post
title: Book Scraper for Markdown Template
permalink: /proj03
---
This project branches off my book scraper for a Notion page. After I finish a book, I like to write down a little summary and review for it so I can remember the details for later. I would store these mini book reports in Notion. Recently, though, I have decided to start writing my book reports down in markdown completely, instead of using Notion as middle man. While Notion does make my reports look pretty, I realized that there was no easy way of storing this data on a storage drive, were I ever to need it, and so it would be best to just write the report in markdown from the get-go.

The basis of this project is simple: it uses Selenium to scrape a dynamic website for book information, and then creates a markdown page including that information alongside a template of questions for you to fill out about the book. When you run the script, it first prompts you to choose between a nonfiction (nf) or fiction (f) template. Then, it will prompt you for a Goodreads link to scrape for book title and book author. After running the script, there should be a file created with the book title as the name in the same directory as the script itself. 

More information about the project can be found on the GitHub repo README.txt file, specifically the template information. Please reach out with any questions via the repo on GitHub!

Since I had already created a somewhat similar project where I scrape a dynamic website and do something with that information, this was not that hard to write. The only real challenge was learning how Selenium worked in contrast to Playwright, as that was my chosen scraper from before. However, once I studied the Selenium documentation more, it did not take too long to program. In fact, because this script does not interact with any APIs, it was much simpler than the previous book scraper I had written for Notion. One just had to create a md file in the current directory--a much more simple task than creating a Notion page. No JSON objects needed!

From this project, I learned how to adapt my previous code to a new usage format. I also got to learn how to use Selenium as a web scraper. It was overall very fun to create something that I will continue to use!