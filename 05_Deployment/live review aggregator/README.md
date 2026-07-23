
# Live Review Aggregator website


## current stack:

✅ Sentiment Analysis API
✅ React frontend (Vercel)
✅ FastAPI backend
✅ Text Summarization model
✅ Product categories (clusters)

The next step is simply adding storage and connecting everything together.


---

## Overall Architecture

                React (Vercel)

         Submit Review Form
                 │
                 ▼
          FastAPI Backend
                 │
     ┌───────────┴─────────────┐
     │                         │
Sentiment Model          Summarization Model
     │                         │
     └───────────┬─────────────┘
                 │
            SQLite/Postgres
                 │
                 ▼
        Dashboard / Aggregator


--- 

## Version 1 (Simple MVP)

Forget authentication.

Forget users.

Just imagine people anonymously submitting reviews.


**Review Form**



Product Name

Category
▼
Electronics
Books
Sports
Kitchen

Rating
★★★★★

Review

_____________________

_____________________

[ Submit ]



---


**When Submit is pressed**

The frontend sends

{
    "product": "Sony Headphones",
    "category": "Electronics",
    "rating": 5,
    "review": "Amazing sound quality and very comfortable."
}

Backend receives it.

Now the backend automatically runs

**Sentiment Model**

which returns

Positive
Confidence 97%

Then saves

Product
Category
Rating
Review
Sentiment
Confidence
Date

into the database.

---

## Database

SQLite is perfect.
A single table.
reviews

id
product
category
rating
review
sentiment
confidence
date

That's enough.


---

## Recent Reviews

Your homepage immediately shows

Recent Reviews

★★★★★

Sony Headphones

Amazing sound quality...

Positive

2 minutes ago

--------------------

★★★★☆

Nike Shoes

Comfortable but expensive.

Positive

10 minutes ago

--------------------

★★☆☆☆

Blender

Stopped working after one week.

Negative
Category Pages

Click

Electronics

and see

Electronics

Total Reviews

125

Average Rating

4.4

Positive

82%

Negative

18%

Then

Latest Reviews

★★★★★

Excellent!

★★★★☆

Very good.

★★☆☆☆

Not worth it.

---

## Summaries

This is where your summarization model becomes useful.

Every time someone opens

Electronics

the backend does

SELECT all electronics reviews

↓

Combine them

↓

Send to summarization model

Prompt:

Summarize what customers think about electronics products in less than 150 words.

Result:

Customers generally praise electronics products for their sound quality, battery life, and overall value. The most common complaints involve durability, warranty issues, and delivery delays. Overall customer satisfaction remains high, with most reviews being positive.

Displayed at the top.

Even Better

Instead of summarizing every request...

Generate it once every 20 reviews.

Store it.

category_summary

Electronics

summary

last_updated

Much faster.

Dashboard

Imagine

Electronics

Average Rating

★★★★☆

Positive

83%

Negative

17%

Most Common Words

battery

camera

quality

delivery

price

Summary

Customers appreciate...
Search
Search

Sony

Results

Sony Headphones

26 Reviews

★★★★☆

Summary

Customers love...
Filtering
Category

Rating

Sentiment

Date

Sort By

Very useful.

Charts

Using Chart.js

Pie chart

Positive

Negative

Neutral

Bar chart

Ratings

5

4

3

2

1
Nice ML Feature

After someone submits

"This blender is terrible."

Immediately show

Detected Sentiment

Negative (99.1%)

before saving.

Feels interactive.

Even Cooler

After 100 reviews

Generate

Top Pros

• Battery lasts long

• Great sound

• Easy setup

Top Cons

• Slow delivery

• Price

• Warranty

using GPT.


---

# Tech Stack

## Frontend

React
Tailwind
Axios
Chart.js

## Backend

FastAPI
SQLAlchemy
SQLite (or PostgreSQL later)
Pydantic

## ML

Sentiment API (your existing model)
Summarization model

---

## Deployment

Frontend → Vercel
Backend → Render
Database → SQLite initially, PostgreSQL (e.g., Supabase or Neon) later
Suggested Development Roadmap

**Phase 1 (1–2 days)**
Review submission form
SQLite database
Save reviews
Display recent reviews

**Phase 2**
Integrate your sentiment model so each review is automatically classified
Show sentiment badges and confidence scores
Add filters by category and sentiment

**Phase 3**
Create category pages
Generate and cache summaries using your summarization model
Display average ratings and review counts

**Phase 4**
Add analytics with charts (rating distribution, sentiment breakdown)
Search by product name
Export reviews as CSV

**Phase 5 (Portfolio polish)**
Responsive UI with dark mode
Pagination or infinite scroll
Loading states and error handling
API documentation (FastAPI Swagger)
CI/CD with GitHub Actions

---

Why this is a strong portfolio project
This combines several AI and software engineering skills into one cohesive application:

Machine Learning: Sentiment analysis and abstractive summarization
NLP: Review processing and category insights
Backend Development: FastAPI REST APIs, database integration, and model serving
Frontend Development: React dashboard with forms, filtering, and visualizations
Deployment: Vercel frontend and Render backend
Data Engineering: Persistent storage, aggregation, and caching

Instead of showcasing isolated models, you'll have a complete AI-powered product that demonstrates how machine learning can solve a real business problem: helping shoppers quickly understand large volumes of customer feedback while enabling new reviews to continuously improve the insights.