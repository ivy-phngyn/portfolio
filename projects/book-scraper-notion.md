---
layout: post
title: Book Scraper for Notion Page
permalink: /proj00
---
The point of this project was to make my Notion library a little more easy to manage. I like to write little book reports summarizing the book I just read in my Notion page. This automation code uses Playwright to scrape Goodreads, a dynamic website, for the book of your choosing. When the script runs, it asks you for a Goodreads link to scrape. Then, it creates a page in your Notion for you to fill out about the book.

You will have to input your Notion credentials and create an integration key to use this script. I detail this process in the README.txt file within the GitHub repository, if you would like to use it. It isn't a hard process, but it can be confusing for sure. Please reach out with any questions via the repo on GitHub!

Honestly, this project was really just for fun. I use it every time I finish a new book, so it does not go unused. I think it truly does save me time when writing my reports: no longer do I have to double check the author's name, or grab the book cover from Google. It was a chance for me to practice using APIs within my code, and I definitely learned a lot in the process. I found reading the documentation to be super helpful in developing this script, alongside understanding the layout of a website. 

Hope someone finds this useful!

# An Aside
Originally, I had used BeautifulSoup and made the script in Python. However, this code eventually broke when Goodreads changed their website layout. The original script was really only meant to be used on a static site. When I learned how I could get information from dynamic websites, I decided to just use Playwright as the scraper, because then all of my code could be in Javascript (the Notion API code I use is already in Javascript). Having it all be in one language was just simplier for me to develop, especially because it was such a tiny project. 