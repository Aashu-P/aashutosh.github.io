---
layout: post
title: "Ethically Ambiguous Data Modeling"
---

When we create models in data science, we are more often than not in the realm of ethically ambiguous data modeling; it's a space where a model might be working perfectly and is completely law abiding, but morally still in the middle ground of right or wrong.

To put this in more real world terms, imagine you just made the perfect ML model to predict credit risk for a bank. You make your model 'blind' to race, but you include zip codes. Because many cities are still racially segregated, the model uses zip codes as a proxy for race. The result of this is a model that might show a 95% accuracy overall, but still denies loans to worthy applicants in minority neighborhoods just because of where they live.

How can we fix this misalignment between technical performance and social outcomes?

1. **Stakeholder Engagement:** Building things for people can't be done in a locked room. We need to actually talk to the people who will actually be affected by the code we write.
   - How this will help ethical uncertainty: Engaging with community members or domain experts can reveal historical biases (e.g. history of redlining in specific zip codes) that a dataset full of numbers can never show. This could prevent us from adding those biases into the model.

2. **Model Interpretability:** Having a "black box" decide people's lives may be legal, but not certainly ethical. That's why it's important to create models where we can explain exactly *why* a prediction was made.
   - How this will help ethical uncertainty: If we are able to see the logic behind why a decision was made, we would potentially be able to spot when a model was using ethically concerning proxies (e.g. using zip code to determine creditworthiness).

3. **Ongoing Monitoring:** The job's not over after the model is deployed. We need to constantly evaluate the model's performance in the real world.
   - How this will help ethical uncertainty: Real world data can change over time and become vastly different from when the model was deployed. Constantly monitoring the model after deployment allows us to catch if the model has unexpected, potentially harmful, outcomes that weren't apparent during testing.
