AI Project Design
DIWM Proactive Intervention (PINT)
Date (last updated): 12/5/2024
DACE
Driver
 Manisha Panta
Approver - Commitments & Execution
 Qingbo Hu
Approver - Technical Solution & Architecture
 Peter Ouyang
Contributors
 Tin Nguyen
Escalation
 Zhewen (Joanne) Fan


Executive Summary
Elevator Pitch
TurboTax Live Assisted users may feel stuck while filing their taxes, potentially leading to abandonment. Moreover, they generally underutilize the help options that are available and which could lead them to make easier progress through their tax filing journey. Our hypothesis is that if we recommend the right help interventions proactively, users will take advantage of the help and address their problems, leading to higher conversion rates.
Model Description
Rule-based model for Phase 1
Launch Date
Jan 15
Status
🟢  POC launch date Jan 15
Test Readout and Metrics
Business Metrics: ROI, S2C
Business Guardrail Metric: RPV, Abandonment Rate
Model Metrics: Interaction Rate
Model Guardrail Metrics: Milestone Progression
Contacts and dependencies
PM : Prachi Raman
PD : Azeem Memon
XD | Content Designer: Craig Moll | Holly Zorbas
Analytics : Alex Zhou


Business Problem 
Overview
During tax prep, users often feel unsure and stuck because they need help or have questions that they don’t know the answer to. In the DIWM (Do-It-With-Me) versions of Turbotax, users actually have access to various options for help, including contact with experts and digital chat interactions through Intuit Assist. However, these forms of assistance are highly underutilized. In fact, during TY23, 80% of users did not utilize the available expert help, and many of these customers had never contacted an expert before.

Based on these observations, we believe that by identifying key moments where users feel stuck and providing them with timely, relevant intervention through either a human expert or digital assistance, we can boost their confidence. This approach involves using personalized and context-specific messages designed to prompt users to utilize the inline interventions provided effectively. By intervening proactively through the user’s tax filing journey and encouraging interaction with available help resources, we aim to ensure more customers complete their tax filings successfully.
Target metrics
The primary goal of this initiative is to reduce user FUD by offering appropriate help, as reflected by an improved conversion rate (S2C). This should normally go hand-in-hand with higher revenue, but it’s possible that this is not the case, so we will need to monitor RPV as well as an auxiliary metric.

As we will explain below, the models we eventually build may be trained to optimize other user experience metrics that are more directly tied to the intervention recommendation, with the hypothesis that those user experience metrics will ultimately correlate with S2C.

Opportunity Sizing : TY24 DIWM Sizing
Product Experience Overview
The new experience aims to infuse meaningful help through inline offers for assistance as opposed to the current product where users see only generic offers.

The experience will test expert help (recipe B) vs digital help (recipe D) and different variants of the content inside each recipe. The current decision has been to integrate the interventions on selected screens which are high abandonment surfaces as a first pass.

More details are available in the PRD and Figma, and also in the Content Generation section below.
PRD : DIWM Personalized Help - PRD
Figma : Proactive Help / Infuse Meaningful Help TY24
Finalized list of screens : Validation - DIWM top abandonment screens
Abandonment analysis on a screen level : DIWM top abandonment screens
Sample of planned expert help experience:

AI Solution Design
The fundamental problem in creating an AI solution for this customer problem is that because this is mostly a new experience, there is no existing training data on the effectiveness of the interventions we would like to recommend. Therefore we suggest that we should begin this project with a data collection/exploration phase so that we can follow with effective models later.
Phase 1: Data collection/exploration
In the initial exploration phase, we aim to collect data that could eventually be used to train models which personalize the intervention experiences. At present, we see personalization opportunities along three potential dimensions: Frequency, Intervention Type, and Content. Some considerations about each of these follow:
Frequency – When and how often should the interventions appear?
A subquestion here is, should we show interventions at all? This is something that we implicitly test by having a control group with no interventions.
A secondary subquestion is, how many times or with what frequency should we show interventions? This could be related to deciding which screens should have embedded interventions or by implementing frequency capping on screens or by capping the total number of interventions shown.
Another subquestion is, what triggering conditions should be used (which also affects the total number of interventions shown to the customer.)
The most relevant metric for frequency seems to be an ultimate business metric of such as conversion, rather than user interaction. In the case of intervention vs no-intervention (control), the control has no intervention for the user to interact with. Moreover, the potential negative effect of showing too many interventions is an impact to conversion.
For the first iterations, this will likely be controlled by business rules.
One way to build a model could then be to have different frequency rulesets and then try to predict conversion for each of them.
A suppression model trained on click rate (to suppress interventions to users who don’t click on them) could be another approach to frequency regulation.
Intervention Type – What kind of intervention will users respond to?
Currently this means digital help vs expert help, but there might be other options in the future.
The most natural metric here is actual nontrivial interaction with the help (user starts a conversation with the expert, or asks a question in Intuit Assist for digital help.) Here we don’t want to use the initial click as the target metric. The goal of the model should be to predict which type of help the customer wants. If they initially click but then don’t interact, it could mean that they didn’t understand the offering and when they actually saw what it was, they decided that they didn’t want it. It might also be possible to consider a weighted reward that uses both the initial click as well as later engagement.
There is an opportunity to build a model to estimate engagement probability for each type of intervention.
Content Personalization – What messaging do users respond to?
This could be personalized based on detailed user features (e.g. referencing tax situations, life events, etc) or just different variants of generic content.
Clickthrough rate seems like the most natural metric/reward. Here we’re trying to pick the content that users find most appealing (assuming that it is well correlated with the eventual intervention.) It seems much more natural to measure user preference for messaging close to where they see the message rather than using a downstream reward.
This is a natural candidate for a bandit-type model. If initial data analysis suggests that user data might be predictive of content preferences, there may be an opportunity for a contextual bandit; otherwise we could attempt a vanilla multi-armed bandit.
First peak test details
Primary dimensions tested
Intervention type (Recipe B vs Recipe D)
Content Personalization (randomly show different content options, with simple personalization when possible)
Control vs Interventions
Currently we are not testing other aspects of intervention frequency, but this is under discussion.
Phase 1 rule-based model 
The PINT model will personalize the DIWM intervention content by making real-time recommendations for the offer type and copy of the intervention text
For exploratory purposes, the first peak version of the model will make rule-based (and partially randomized) recommendations to collect data on the relevance and effectiveness of the interventions
The model uses criteria such as user tax profile and life event data to personalize 
Finalized test recipes and rules to show content: Content Gen + Model Features
Proactive Intervention Rulebased Model Phase 1 

Phase 2: Initial model iteration
Depending on the analysis of data from Phase 1, we will choose one or more of the above dimensions to create models. Built into our plan is to devote time in December and early January to constructing the ETL necessary to build these models so that in season we can train with a shorter iteration time, aiming to deploy in February.

Different scenarios depending on results of 1st peak:
Higher frequency wins over low frequency overall or vice versa
Then pick the frequency winner, possibly test frequency in more detail
Different winners for different customer segments, mixing frequency and content
flat model instead of hierarchical
Different frequency winners across customer segments, but no winner for content
personalization model for frequency
Personalized content wins overall, across frequency variants
Lean into more diverse personalization, maybe online content gen

Digital help will be new after the 1st peak. Need data collection phase for expert vs digital help. Open questions for how to deal with digital help:
How do we design a model to recommend between digital and expert help?
Can we design experimental options within digital help for data collection and future modeling?

Strategies for developing a model to predict which screen to display interventions on
General question – can we build a model to predict when to show the intervention?
We want to have the bandit arms compare between roughly comparable things, so one candidate is to have the arms be different screens or topics in which to show the intervention
Need a strategy to decide when to intervene (random per screen?)
Don’t want too many arms – maybe go by topics and not screens
Reward would be engagement

In the case of bandit/reinforcement learning approaches, we may build upon the guidance in CG Reinforcement Learning Operation Playbook.
Phase 3: Longer term vision
Mostly TBD, but the main ideas so far are more complex layered recommendation models, automated retraining/reinforcement learning loops, and greater automation for content generation. 
Rule 
Previous Work
An example of previous work on recommending interventions was the CG Abandonment model, which aimed to estimate which users had a high probability of abandonment and then surface interventions to those users. (The model also estimated probabilities for particular flavors of abandonment, which were used as proxies for price sensitivity and similar user profiling.)

This model was quite complex and expensive to run because of its need for real time clickstream data. Moreover, because its predictions were only indirectly related to the interventions used, it was not clear if the model scores were well correlated with user preferences for the interventions, not to mention whether the interventions themselves were good experiences.

The experience with integrating the Abandonment model into the product was one of the motivations for designing models which aim to predict a reward probability that is directly tied to the interventions used.

Another project that aimed to have an early season data collection phase followed by introducing a trained ML model later was the TTO Engagement model.
Engineering and Architecture

Most details are TBD for now.

We anticipate integration through an MXS endpoint orchestrate through the MSAAS service, with the request and response as defined in this model contract:
 Proactive Intervention Model Contract

The main feedback for retraining the models will come from beacons, but depending on what model we eventually build, it might be important to have feedback available in realtime. For example, one scenario could be that the model would manage frequency capping of the interventions, so it would need to know how many impressions a user had seen. If this is the case, we plan to set up a feedback endpoint within the MSAAS service which PD can hit to send the necessary data and which we can store in FMP. (A preferable option would be for PD to directly push the data into Kafka to be ingested into FMP, but this might not be possible.)
Content Generation
The product team plans to test four different recipes. For the initial peak period, Recipes B and D have been chosen as the primary focus for experimentation. Therefore, we have created content that aligns with these priorities.
Expert-first interventions with a direct connect with expert CTA showcasing a specific expert who is available
Expert-first interventions with a direct connect with expert not showcasing a specific expert but any expert who will be available
Digital-first interventions in Q&A format with a CTA to make direct connect with expert
Digital-first interventions in Q&A format with a CTA to go to Intuit assist and then to an expert if needed
Control would be - NO intervention
Personalized Messages [Recipe B]
To generate the relevant and personalized content that prompts users to accept offered expert intervention, we utilize prompt engineering techniques with the existing GenAI model (GPT 4o). This involves carefully crafting prompts that integrate TurboTax brand character, tonality, voice, empathy and uses specific user profile attributes, current user interactions on the screen, and relevant life events.  Our aim is to guide GenAI in generating content that is both contextually relevant and highly personalized.

Further supporting our initiative, we have developed a content generation tool that provides a shared workspace for prompt versioning. This centralized platform allows the Content Design and AI teams to engage in effective collaboration through iterative feedback, organized experimentation, and transparent progress tracking, thereby enhancing our efforts.

For 1st peak, we specifically generate content on four carefully selected screens recognized for their high rates of user abandonment yet spaced optimally throughout the user journey. For each screen, GenAI is configured to produce approximately three distinct content variants, each tailored to the specific user profile, context of the screen and data points to focus on, in order to maximize relevance and personalization. Detailed listings of the WIP generated content and the specific features  utilized are documented here which is currently in the process of final review.
Sample of generated content on Wages and Income Topic.

Contextual QnA [Recipe D]
We plan to use TaxQnA to generate answers to specific, pre-selected questions for various screens. Initially, these responses will be created offline in a batch fashion. This setup allows us to ensure the quality and relevance of the content. Furthermore, if any of these pre-generated answers fail to pass our internal review process due to quality concerns, we will revisit and revise them as needed to meet our standards.

The list of questions and screens to target are yet to be finalized. 

Generated content :
 Content Gen + Model Features
Content Combination Based on Life Events

