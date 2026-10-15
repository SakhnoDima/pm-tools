# Client message examples

Real PM messages from a client chat, anonymized (names and project details replaced).
They show the voice; they are not templates to copy word for word.

## 1. Quick acknowledgement

> Sure, I'll check

Copy: one line is enough when the client just asked for something. No filler.

## 2. Did the homework before asking

> Did [the client's analyst] check the [project] database? This script writes data to it. I checked the script on the server and there are no errors. Also, looking at the tables, I can see the latest data from [date]

Copy: facts we already verified first, then one concrete question.

## 3. Investigation result + proposal with consent

> Hi, I've completed the investigation on the server. It seems the script process experienced a silent freeze a few months ago without leaving any specific error in the logs. It likely resumed its normal operation when I accessed the server recently.
>
> To make sure this doesn't happen again, I would like to spend some time improving the script. I plan to add an automatic restart mechanism and better monitoring so we are instantly alerted if it ever stops. Let me know if you are okay with me proceeding with these updates.

Copy: diagnosis in plain words, honest uncertainty ("it seems", "likely"), proposal framed as client benefit, ends with a request for consent.

## 4. Client complains about quality (informal, the PM's most natural voice)

> its a good question about quality issue)
>
> when we developed the solution we just provided the working script/flow, without support. Usually these scripts need maintaining time after time (many reasons - data can change in provider side for example).
>
> I'll think about monitoring and healthcheck. I understand thats maintaining its my responsibility. For this and rest projects
>
> also I'll think/check about data loss and how to restore the data. I on it)

Copy: takes responsibility, honestly explains the boundary (no support agreement), commits to next steps, human and calm.
Do NOT copy: typos, missing apostrophes, ")" emoticons. Write the same thing in clean English.

## 5. Structured proposal (polished)

> Hi, I've found the cause. There are several places in the pipeline where a process can hang silently, waiting on an external connection with no time limit, and keep holding memory instead of finishing. When that happens the server looks perfectly healthy from the outside, but the scheduled updates stop. [...]
>
> To make sure this never happens again, here's what you'd get: [...]
>
> There's one more thing I noticed that I'd like your opinion on. [...] I'd prefer to add a check that stops the update and notifies us when the incoming data is drastically smaller than usual, rather than writing it. Would that be acceptable to you, or do you have cases where a genuinely small file is expected?
>
> Altogether this is around [N] hours.
>
> And about the missing period, I remember you used to send me historical data files. Do you happen to have those for that period? If so, I can load them into the database manually and close the gap.

Copy: cause in one plain paragraph, "here's what you'd get", a real decision question with the trade-off, estimate in hours, a concrete ask that unblocks us.

## Combining 4 and 5

Take the structure from #5 and the plainness and humanity from #4.
