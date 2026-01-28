---
layout: page
title: Blogs
---

## Introductory Post
#### Why does learning data science in social and interdisciplinary contexts matters?
When I think of data science, my mind goes straight to numbers, models, and predictions. But most of the data in data science actually represents people. Many, maybe even most (scary), aspects of their lives: behavior, choices, habits, mistakes, and so on. That’s why learning data science in social and interdisciplinary contexts matters.

Why would you even want to model social topics and people? Sounds a little "big brothery” to me. But when you think about it, data science is finding insights in the data, it's a way to better understand the world we live in. Modeling social topics helps us turn real world problems into something we can try to solve using reason. Things like churn, public health, or access to resources are not clean and simple problems. They are influenced by culture, bias, etc. If you ignore all those factors and just treat the data as numbers, you end up building models that might look good in theory but fail in practice

One of the biggest responsibilities that comes with using data about people is privacy. When looking at a dataset of just numbers, I think it's easy to forget that each row is a person’s life. It's important to understand that what you do with this data might have big impacts on the lives of real people. 

Through this course, I obviously want to further my understanding about the technical side of data science (eda, modeling, etc.), but I’m hoping to get better at connecting the technical work with real world context. I want to understand not just how to build models, but also how to make it both ethical and effective. I also want to better understand how to learn the context of the data. Being able to properly learn the context would ultimately help in connecting it with the technical work.

---

## Ethically Ambiguous
When we create models in data science, we are more often than not in the realm of ethically ambiguous data modeling; its a space where a model might be working perfectly and is completely law abiding, but morally still in the middle ground of right or wrong. 
To put this in more real world terms, imagine you just made the perfect ML model to predict credit risk for a bank. You make your model 'blind' to race, but you include zip codes. Because many cities are still racially segregated, the model uses zip codes as a proxy for race. The result of this is a model that might show a 95% accuracy overall, but still denies loans to worthy applicants in minority neighborhoods just because of where they live.
How can we fix this misalignment between technical performance and social outcomes?
1. Stakeholder Engagement: Building things for people can't be done in a locked room. We need to actually talk to the people who will actually be affected by the code we write.
   - How this will help ethical uncertainty: Engaging with community members or domain experts can reveal historical biases (Ex- History of redlining in specific zip codes) that a dataset full of numbers can never show. This could prevent us from adding those biases into the model.
2. Model Interpretability: Having a "black box" decide people's lives may be legal, but not certainly ethical. That's why its important to create models where we can explain exactly *why* a prediction was made.
   - How this will help ethical uncertainty: If we are able to see the logic behind why a decision was made, we would potentially be able to spot when a model was using ethically concerning proxies (Ex- Using zip code to determine creditworthiness).
3. Ongoing monitoring: The job's not over after the model is deployed. We need to constantly evaluate the model's performance in the real world.
   - How this will help ethical uncertainty: Real world data can change over time and become vastly different from when the model was deployed. Constantly monitoring the model after deployment allows us to catch if the model has unexpected, potentially harmful, outcomes that weren't apparent during testing.
