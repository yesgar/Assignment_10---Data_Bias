# Assignment_10---Data_Bias
**CONTENT WARNING:  
The Perspective API is designed for use in content moderation, and the dataset contained very “toxic” comments. Some of the comments in the sample dataset used as well as my testing comment set are racist, sexist, ableist, and offensive. Most comments contain profane language.**  
Documentation for the Perspective API can be found here: https://developers.perspectiveapi.com/s/

**TESTING**  
The goal of this assignment was to explore the concept of bias through querying an existing natural language processing model — specifically, the Perspective API released by Google Jigsaw. Based on my data exploration of examining a sample dataset of internet comments and their scores, I developed and tested my hypothesis regarding Perspective's performance on a test set of 12 example comments derived from sample data provided in the ipynb file. I then documented the model scores and assessed whether or not my hypothesis was correct based on my sample.  
The 12 example comments are based on the comments tested in my Data Exploration in the section titled "3.3 Sex Bias Query." However, these comments are altered so that they use the same topic and subject, but this time making it toxic to see if it will score over my "borderline toxic" threshold (while also testing my hypothesis).  
Considering my hypothesis, I chose my example comments by having a combination of toxic comments:
- with a word amount identified as long (>=30), short (<=5), or medium (10-15)
- targetted to females and males
- being grammatically correct or easy to understand and grammatically incorrect or hard to understand 

**HYPOTHESIS**  
Based on my data exploration and understanding of how the Perspective API is trained and used, I believe Perspective’s performance will show little bias towards toxic female comments in comparison to toxic male comments (being fairly equal in its scoring), but will mostly do this or perform well with comments that are average or reasonable in length and with more formal (or understandable) grammar or phrasing. Therefore, I believe Perspective API will make more mistakes on comments that are too short or that are too long where both types are informal in grammar (unclear in meaning or easy to misunderstand) and may score them unfairly especially based on my threshold.

**FINAL INSIGHTS/FINDINGS:**  
Comment Types & Their Toxicity Levels:  
>- a LONG, toxic, anti-FEMALE comment that is grammatically CORRECT or easy to understand: 0.8988238
>- a SHORT, toxic, anti-FEMALE comment that is grammatically CORRECT or easy to understand: 0.8460273
>- a MEDIUM, toxic, anti-FEMALE comment that is grammatically CORRECT or easy to understand: 0.7856813


>- a LONG, toxic, anti-MALE comment that is grammatically CORRECT or easy to understand: 0.8778702
>- a SHORT, toxic, anti-MALE comment that is grammatically CORRECT or easy to understand: 0.8629672
>- a MEDIUM, toxic, anti-MALE comment that is grammatically CORRECT or easy to understand: 0.83334327


>- a LONG, toxic, anti-FEMALE comment that is grammatically INCORRECT or hard to understand: 0.8115627
>- a SHORT, toxic, anti-FEMALE comment that is grammatically INCORRECT or hard to understand: 0.7761081
>- a MEDIUM, toxic, anti-FEMALE comment that is grammatically INCORRECT or hard to understand: 0.76523775


>- a LONG, toxic, anti-MALE comment that is grammatically INCORRECT or hard to understand: 0.78855824
>- a SHORT, toxic, anti-MALE comment that is grammatically INCORRECT or hard to understand: 0.78711975
>- a MEDIUM, toxic, anti-MALE comment that is grammatically INCORRECT or hard to understand: 0.83334327

To ensure scoring was evenly done, I made sure to use the same topic and meaning throughout my testing comments as well as keeping the same pattern of grammar (within the correct and incorrect classes) to see if there were bias in sexes or scoring difference with comment length. For more information on my methods or comment identifications, visit the ipynb file uploaded to this repository. I will mostly be addressing my results, insights, findings, and theories below.

Based on my testing, it seems to be apparent that comments with incorrect grammar or hard to understand phrasing always scored lower in toxcity than comments with correct grammar, even when both variations of the comment (correct & incorrect grammar) had the same intent and harmful meaning. They were essentially the same comment with the same length, just with different phrasing. However, it seems that length does not hold a great affect on the toxicity score, but moreso the "directness" of the comment. Therefore, even if a longer comment had more harmful words in it for both the grammatically correct and incorrect comments, 3 times out of 4, they still scored lower than a comment that was shorter in length but more direct in its meaning. For example:
>- 'Women should cut their boobs off.': 0.8460273
>- 'Women should cut their boobs off and be ashamed of going out into public': 0.7856813


>- 'Men should cut their penises off.': 0.8629672
>- 'Men should cut their penises off and be ashamed of going out into public.': 0.83334327


>- 'Women need slice chest boob off.': 0.7761081
>- 'Women need slice chest boob off and feel bad shameful by being into public': 0.76523775

The examples above show that even though the longer comments added had more harmful words or phrasing on top of the shorter comments, they still scored lower than the shorter comments because they were more direct. Therefore, supporting that regardless of length or correct/incorrect grammar, a more direct comment will score higher in toxicity.

Additionally, all my comments scored at least above 0.76523775, which with respects to my threshold, is correct considering I dervied their meaning from a **toxic** comment from my data exploration that scored a 0.60152835 (0.60). According to my threshold, I made for this scoring to be "borderline toxic" since it seemed to be asking a genuine question regarding the choice women make about their anatomy and identity, but just phrasing it in an extremely inappropriate way (as shown below):
- 'So just because a woman cuts her boobs off and stitches a little something on does that really make her a man  Sorry this is a woman that is just really confused'

Therefore, when determining my threshold I determined scores between 0.5 and 0.6 as "borderline toxic". So as previously mentioned, whenever I was making my testing comments, I took the comment above and altered it so that it used the same topic and subject, but this time making it toxic to see if it would score over my "borderline toxic" threshold (which it did).

Additionally, something that surprised me was that Perspective API occasionally showed bias towards toxic comments that were targetted to males in comparison to those same comments changed to be targetted to females, scoring anti-male comments higher in toxicity than anti-female comments. For example:
>- 'Men should cut their penises off.': 0.8629672
>- 'Women should cut their boobs off.': 0.8460273


>- 'Men should cut their penises off and be ashamed of going out into public.': 0.83334327
>- 'Women should cut their boobs off and be ashamed of going out into public.': 0.7856813


>- 'Men need slice pelvis penis off.': 0.78711975
>- 'Women need slice chest boob off.': 0.7761081


>- 'Men need slice pelvis penis off and feel bad shameful by being into public': 0.83334327
>- 'Women need slice chest boob off and feel bad shameful by being into public': 0.76523775

The only occurrence where toxic comments towards women scored higher than those towards men were when comments were extensively longer and clearly direct in their meaning (as shown below):
>- 'Women should cut their boobs off and be ashamed of going out into public because they should understand that having a vagina is shameful, they should all go to hell.': 0.8988238
>- 'Men should cut their penises off and be ashamed of going out into public because they should understand that having a penis is shameful, they should all go to hell.': 0.8778702


>- 'Woman need their chest boob slice off and no feel good feel shame in around people outside because woman genitals are bad shameful, they will are going to underground hell.': 0.8115627
>- 'Man need their pelvis penis slice off and no feel good feel shame in around people outside because man genitals are bad shameful, they will are going to underground hell.': 0.78855824

However, I believe this is still unfair and biased since each of these pairs should have relatively the same score. A theory I have on why this may be occuring is that the API is trained to detect anti-female comments to be extremely toxic considering it is a disadvantaged group, whereas males are considered advantaged so when there are anti-male comments it can be seen as less severe. However, this in itself contributes to bias and inequality whereas it should be evening the scores.

Therefore, considering my hypothesis of:
- Perspective API will make more mistakes on comments that are too short or that are too long where both types are informal in grammar (unclear in meaning or easy to misunderstand) and may score them unfairly especially based on my threshold.

**My hypothesis seems to be partially correct considering comments that were too short or too long and had informal grammar or unclear phrasing tend to score lower than the same comment just made to have correct grammar or understandable phrasing. However, it seemed that this was mostly because certain comments were more "direct" than others, regardless of length and therefore also making my hypothesis partially incorrect. Therefore, although all comments were intended to score as toxic based on my threshold (which they performed successfully), the difference in certain scoring (even if it was just a .1 difference) seemed to be bias towards how direct comments were even if some seemed more harmful than others.**
