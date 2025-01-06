Goally daily standup bot a custom slack app with github actions workflow documentation

Workflow # 1: 

this workflow runs a cron job every 5 days a week at 11 am and drops a message to array of users ID as well as in channel, for this I am using slack API's with O auth secret token, I set my goally standup bot with various scopes so they can be used when i call them from my workflow, so my workflow calls the endpoint it needs for goally standup bot, using curl, sending token in header and message in body my first API request sends a main message in channel and I am saving response of main message(which will have thread) in a txt file for second workflow, and second API call will send message to user asking them question, user provided response will be saved in a txt file as well which is to be used by 2nd workflow, I am pushing both txt in repo, so everything will be in github.

Workflow# 2:

this workflow runs a cron job every 5 mins from 11am to 2 pm 5 days a week, to capture user response and send it in thread, have multiple conditions to check for txt files which got made in first workflow are at right place and then fetch right data from them and show that data in against right user, further it opens a poll and post user reply from txt file to the thread, lastly saving a timestamp against that user that they have respond to avoid redundancy.
why am i using another workflow's cron job to get user replies ? is because at first I build a local node js server for realtime communication but I could not host it, as every platform was paid, and locally it was not accessible in slack app events, I understand running a job every 5 min is not a flexible solution but does the job for us.

Workflow# 3:

this is the workflow I was using before which was only sending a main message in standup channel, it uses a web-hook to just send one API for message, so I did not used the web-hook for the above two flows as they don't allow polling response and assessing user information, hence I used O auth token.

Slack App: https://api.slack.com/apps/A07R4MH694H 



