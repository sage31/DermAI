# DermAI
Your online artificial intelligence based dermatologist.
![Main page](https://i.imgur.com/TETsEf4.png)


## Inspiration
The cost of medical consultations with a qualified physician can often be prohibitively expensive, with even a brief follow-up lasting just a few minutes costing upwards of hundreds of dollars. In particular, patients seeking consultations with dermatologists for possibly harmful skin conditions may hesitate due to the high costs involved. Yet, it is crucial to not overlook the significance of a visit to the dermatologist, since early detection of skin cancer is critical to prevent its potentially fatal consequences. Regrettably, many individuals remain unaware of this fact, and often do not realize they have skin cancer until it has progressed significantly. With over 2 million cases of skin cancer every year in the United States, we feel this is an urgent issue that needs to be solved--mitigated at the very least.

## What it does
First, upload a photo of the area of skin to our website. We will then do all the work to feed the image into our AI model and output a medical diagnosis, with a high accuracy. We provide information about the possible dangers and harms of each condition, as well as links to detailed pages where one can learn more. Also, we provide a tab to find the closest dermatologists using the Google Maps API and a database for users to research the most common skin cancers. Because artificial intelligence models aren't always perfect, we've implemented an algorithm that strategically chooses the next closest match to your submission, in case an error has been made.

## How we built it
Backend: Building the AI was certainly the most challenging part of this project. We found two datasets with a combined number of over 10,000 images of various skin conditions. The first dataset focused mainly on skin cancers, while the second dataset had a wide range of skin conditions. We decided a 2-stage approach for our detection program would be best: the first stage is a model that will categorize an image into one of three broad categories (vascular lesions, benign skin lesions, and cancerous or precancerous lesions), while the second stage focuses on categorizing these images even further, finding the specific condition--for example, a cancerous lesion could further categorized as basal cell carcinoma. We also provide information to the user about the confidence-level of each prediction, in a percentage form. Because our dataset for benign lesions was exceptionally large, our AI models perform exceptionally at identifying these lesions, achieving nearly 90% accuracy on a testing set. The models are built on the pre-trained Inception V3 image recognition model by Google, and we used transfer knowledge to fine-tune it to our data. We use Flask to host a server that runs the model on images passed by POST requests, and returns JSON objects with the results.

Front-end: For the frontend, we used the Google Maps API to gather nearby dermatologists, and wrote the rest of the website in raw HTML/CSS/JS.

## Challenges
As aforementioned, training the AI was the hardest part of this project. At first, we struggled to find data. Then, when we found data, we struggled to organize it in a way that optimized accuracy and categorized the data nicely. After hours of testing and training different models, we finally settled on the 2-stage approach--first splitting into three categories, and then testing the data on the more specific model for each category. It took a lot of time just to organize the data into these categories because they were not structured neatly when we downloaded them. The AI model training alone took around 2 hours, due to the massive dataset size. In the meantime, we solved many problems on the frontend, and worked on making a server to host the model on the backend.

When the models were finally finished, learning how to use Flask from scratch was a bit of a process. At one point, we had spent around thirty minutes trying to solve an issue before realizing that all we needed to do was run the code from a folder within the directory we were working out of. In the end, though, we were able to figure out how to use Flask and successfully connected the backend with the frontend. finding the data sets with variability

## Accomplishments that we're proud of
One of the major accomplishments that we had in this hackathon was our division of work. At the beginning of the hackathon, we thoroughly planned out who would work on which parts of the website, making sure that these parts were at least somewhat mutually exclusive such that we would avoid merge conflicts in the end. Stephen and Huy (participants at the INRIX Hackathon 2022) mentioned that source control was much better this time around compared to the INRIX Hackathon. We're also proud of the fact that we were able to learn how to use so many technologies in such a short amount of time. Ethan was the only one on our team who knew vaguely of using Tensorflow to build AI models, and none of us had used Flask to build a backend. Thus, it was one of the most satisfying moments when our website was finally functional.

## What we learned
From this hackathon, we learned that keeping the momentum of the project high is extremely important, and surprisingly, taking fun breaks is one of the best ways to do this. We took multiple walks during the night, and each time as we walked back into SCDI to get back to work, we felt prepared and refreshed. We also found that we all shared an interest in dance music, and listening to dance music proved to be very motivating for us. Without the right mindset and without the momentum, our team could not have made it as far we did, so we'll definitely keep this in mind for the next hackathon.

## What's next for DermAI
While we are proud of DermAI, it is very much still a work-in-progress. The CSS and overall design could certainly use some work, and the website could have more features. Most importantly, we only trained the AI models on 3 broad categories of diseases, and 18 specific diseases for the purposes of this hackathon. However, in order to truly make DermAI an online dermatologist, it would need to know many more specific diseases. This would require much more data, and a lot more time. Furthermore, we feel that a mobile app would be a good area of expansion for DermAI in the future. While websites are easy and convenient on computers, a mobile app with a live camera would be ideal for use on a phone.
