---
layout: post
title: "Tracking job applications using Trello"
date: 2014-08-14 08:12:46 -0400
comments: true
categories: [productivity, job search]
Author: Jody White
---
I've had the unfortunate experience of being laid off recently due to a re-org of sorts. My typical response is to take a day to myself where I decompress from the situation, enjoy the extra time I'll have
and hit the job search hard the next day.

Other than not having a steady source of income, one of the problems I've encountered is how to track my applications. The first time this happened to me I didn't do any real tracking. Toward the end of my job search I 
started using a web app to track the submitted applications, where I was in the process, and any notes about contacts for the posted position. But 2 years later at my next job search I wasn't able to find the app nor have I been able to find it this time. So I had to move on to something else.

I started this job search using an Excel spreadsheet. Excel can be pretty awesome when needed but it does kinda scream "boring" right? I looked into a different web apps but decided to come up with my own workflow using Trello.

The workflow itself is very easy to set up and is fairly extensible due to the robustness of Trello.

Get yourself to [Trello](https://trello.com/login) and create a free account.

In the upper right hand corner click the `+` sign and choose New Board. Give your board a name, something descriptive.

You'll see the typical Kanban lists by default. You can't delete a list, only archive it so you might as well rename these three lists to the first three lists we'll use for our tracking.

Rename the first three lists to:

- Applications
- Application Sent
- Phone Interview

Then in the text box `Add a list` let's start adding the rest of our lists.

- Thank you email (Phone Interview)
- Waiting to hear back (Phone Interview)
- Formal Interview
- Thank you card (Formal Interview)
- Waiting to hear back (Formal Interview)

Your final list selection will look something like this: {% img /images/ListSetupTrello.png 'image' 'images' %}

I've set the workflow up so that you should only have to move left to right. There might be some instances where you have a phone interview following up a formal interview or a follow-up interview after your first Formal Interview, and at that point I do move the cards back and put them through the workflow again.

Now let's review the lists.

###Applications
As you find a job application you want to apply for you add it to this list. I name the card `Job Title - Company`. So if I were applying for a Software Engineer position at Google the name of the card would be `Software Engineer - Google`.

I then take the job description and paste it into the Description of the card.
{% img /images/jobDesc.png 'image' 'images' %}

###Application Sent
When I've finished writing an employer specific cover letter and finished tweaking my resume for that employer I submit the documents. At this point I move the card from `Applications` to `Application Sent`. The move will record the time and date of the submission but I go ahead and add a comment to the card with the **Applied Date** and with a link to the URL if I found the job online somewhere.

###Phone Interview
More times than not the first step in the interview process is a phone interview. When I'm contacted for a phone interview I change the due date on the card to the time and date of the interview. Then I move the card from `Application Sent` to ` Phone Interview`.

After speaking with the employer I add whatever information I've gleaned from the conversation to the comment section of the card. I also add any contact information I've collected and I move the card from `Phone Interview` to `Thank you email (Phone Interview)`. I also delete the due date on the card.

###Thank you email (Phone Interview)
It's always good practice to follow up any kind of interview with a Thank You. So there's a list specifically for proper interview etiquette. After I've sent the thank you email I move the card forward to `Waiting to hear back (Phone Interview)`

###Waiting to hear back (Phone Interview)
Sometimes there's no special information to add here. If I have contact information for the employer I will add a due date to the card so I can have a reminder to follow-up with them. Or if the employer gives me a timeline I will add that timeline to the due date so I can know when to expect to hear back from them and follow-up if I don't.

Unfortunately, sometimes I don't hear anything back from this list and archive the card. I'm an optimist so I feel keeping the card in this list for a month is enough time to hear back from someone. If I don't hear back after a month I archive.

###Formal Interview
Great! We've been called in to meet face to face! I move the card from `Waiting to hear back (Phone Interview)` to this list, set or change the due date to the date and time of the interview, add whatever comments in the section that is applicable for the formal interview and start preparing!

###Thank you card (Formal Interview)
Once you're home and your nerves have settled down move the card from `Formal Interview` to `Thank you card (Formal Interview)`. Remove any due dates and add any and all notes you've taken from the formal interview to the comments section of the card.

We're back to best practices for interviewing! If you've been called in to an interview the employer deserves more than just an email. Get the business cards of everyone that has spoken with you. If the company is within reasonable driving distance of you then you might want to consider dropping the thank you cards off at the front desk. Otherwise, do this the old fashioned way and buy some stamps and mail them in!

###Waiting to hear back (Formal Interview)
After you've mailed or dropped off your Thank You Cards you can move the card for the job from `Thank you card (Formal Interview)` to `Waiting to hear back (Formal Interview)`. This can follow the same rules as `Waiting to hear back (Phone Interview)`. Set up a due date if you want to follow-up or if you were given a time line by the employer. It's rare to not hear back from an employer at this stage, although it has happened to me once. 

When you've heard back from the employer and in the unfortunate scenario they're moving forward with another candidate, add a note to the comment section on the final decision, date it, and archive the card.

**Do not delete the card as you will want to keep the contact information and notes in case you apply in the future. Or if the employer reaches out to you again.**

##Notes
So I've gone through a few iterations of this workflow and this is what works for me. If you like this but it doesn't quite work for you...tweak it!

One of the things I tried earlier was to only have one `Waiting to hear back` list. Then I would use Labels to note what I was waiting to hear back from. I also included `Application Sent` in that list since I was waiting to hear back about my initial resume submission. But then I would move cards forward then back, then forward again. What I like about the above workflow is that for the most part it moves left to right and I can more easily see which stage the application is in.

An idea I have that I plan on doing unless someone beats me to it, and if someone wants to then please be my guest, is to create a Trello clipper extension for a browser that will clip the Job Title and Job Description from an online job posting and send that directly to Trello as the Card Title and Card Description.

