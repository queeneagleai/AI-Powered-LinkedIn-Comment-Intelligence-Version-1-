# AI-Powered-LinkedIn-Comment-Intelligence-Version-1-
What if every LinkedIn comment was automatically analyzed, prioritized, and brought to your attention before you even opened LinkedIn?

The Story

As my LinkedIn audience continued to grow, I noticed something that every creator eventually experiences.

The more engagement your posts receive, the harder it becomes to keep up with the comments. Questions get buried beneath praise, potential clients are easy to overlook, and collaboration opportunities can disappear simply because you didn't see them in time.

Checking LinkedIn notifications throughout the day isn't scalable.

So I decided to build an AI workflow that watches my LinkedIn comments for me.

Instead of reading every comment manually, the workflow scrapes new comments, lets AI understand what each comment means, prioritizes the important ones, stores the analysis, and instantly alerts me whenever a comment needs my attention.

This is Version 1 of that build.

🎯 The Problem

LinkedIn creators, consultants, agencies, and business owners receive dozens (sometimes hundreds) of comments every week.

Most people still:

Read every notification manually.
Decide which comments deserve replies.
Accidentally miss genuine questions.
Overlook potential leads.
Lose collaboration opportunities.
Spend unnecessary time sorting through praise and low-priority comments.

As engagement grows, this process quickly becomes overwhelming.

The Solution

This workflow acts as an AI-powered LinkedIn community manager.

Here's what it does:

1. Schedule Trigger

The workflow runs automatically every 30 minutes.

No manual checking required.

2. Scrape LinkedIn Comments

Using an Apify actor, the workflow collects comments from selected LinkedIn posts.

3. Filter the Results

The scraper returns both:

Post summaries
Individual comments

The workflow filters out everything except actual comments.

4. AI Analysis

Each comment is analyzed by GPT-4o Mini via OpenRouter.

The AI classifies every comment into exactly one category:

Question
Praise
Potential Lead
Hater
Collaboration Opportunity

It also assigns a priority:

High
Low

along with a short explanation for its decision.

5. Merge AI Results

The workflow combines the AI output with the original LinkedIn comment data so both the comment details and AI analysis stay together.

6. Store the Results

Every analyzed comment is logged into Google Sheets, including:

Comment author
Comment text
Post URL
AI label
Priority
Reason
Processing timestamp

This creates a searchable history of all processed comments.

7. Notify High-Priority Comments

If AI labels a comment as High Priority, the workflow immediately sends a Telegram notification so important conversations can be addressed quickly.

Low-priority comments are simply logged for future reference.

💡 Beginner note: A Trigger is simply the event that starts a workflow. In this project, the trigger is a schedule that runs every 30 minutes.

🧰 Tools Used
Tool	Role in this workflow
n8n	Workflow orchestration
OpenRouter (GPT-4o Mini)	AI comment classification
Structured Output Parser	Ensures consistent JSON output
Apify	Scrapes LinkedIn post comments
Google Sheets	Stores processed comments
Telegram	Sends high-priority alerts
🖼️ Demo

Workflow Screenshot

<img width="593" height="226" alt="image" src="https://github.com/user-attachments/assets/85b62eeb-8b02-4d28-9f46-74d7547acbf1" />


Sample Output

AI labels comments automatically.
High-priority comments trigger Telegram notifications.
Every processed comment is logged into Google Sheets.
How to Set It Up
1. Import the workflow

Import the workflow.json file into your n8n instance.

2. Connect your accounts

You'll need credentials for:

OpenRouter API
Apify
Google Sheets
Telegram Bot
3. Configure the Apify actor

Replace the sample LinkedIn post URLs with your own public LinkedIn post URLs.

4. Connect Google Sheets

Create a sheet with the following columns:

comment_id
author
comment
post_title
post_url
comment_date
label
priority
reason
replied
processed_at
5. Configure Telegram

Replace the sample Chat ID with your own Telegram Chat ID.

6. Activate the workflow

Run the workflow once to test everything, then activate it.

The workflow will automatically monitor your LinkedIn comments.

⚠️ Common mistake: Make sure the Google Drive API is enabled in your Google Cloud project. Without it, the Google Sheets node won't connect properly. Also ensure your AI node uses a Structured Output Parser to prevent invalid JSON responses.

📈 What I Learned / Why It Matters

Building this workflow taught me that AI automation isn't just about generating intelligent outputs—it's about creating reliable systems that work consistently in the real world.

Some of the challenges I solved included:

Configuring Google Drive and Google Sheets correctly
Handling AI structured output reliably
Filtering Apify dataset results
Merging AI output with scraped data
Preserving original comment metadata
Routing comments based on AI priority

The biggest lesson?

The real value isn't classifying comments.

It's automatically deciding which conversations deserve immediate attention.

🚀 Version 2 Roadmap

Planned improvements include:

 Duplicate comment detection
 AI-generated reply suggestions
 Human approval before replying
 Automatic LinkedIn replies
 Supabase database integration
 Analytics dashboard
 Comment trend reporting
 Multi-channel notifications (Email, Slack, Microsoft Teams)
 About This Project

Built by Queen Ikwuji, founder of QueenEagleAI.

I help businesses eliminate repetitive work using AI automation, n8n, and no-code tools while teaching others how to build practical AI workflows from beginner to advanced level.

💼 LinkedIn: https://www.linkedin.com/in/queen-ikwuji-8b925524a/
📧 Email: queenikwuji@gmail.com
🌍 Building practical AI automation projects in public.
⭐ Support the Project

If you found this workflow useful:

⭐ Star this repository
🍴 Fork it and customize it
🛠️ Build your own version
💬 Share your ideas or improvements

I'd love to see what you build with it!
