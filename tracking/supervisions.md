# PhD Tracking

## Upcoming Supervision: 

Meeting Agenda: 

Admin:
<ul>
	<li> First year reveiw, when will this be? Do I need to do anything? </li>
</ul>

Since last meeting:
<ul>
	<li> Put everythig I've done on Github and my website </li>
	<li> Tried to contribute to Fat-forensics (pull request with kacper) </li>
	<li> Applied to DSG </li>
	<li> attended ICML - write up here </li>
	<li> Research:
		<ul>
			<li> Thought a lot about understanding vs. explaining and what it means in relation to data. wrote this </li>
			<li><b> Research Project 1: extracting meaning from longitudinal health data (link here) </b>
				I guess the main idea behind this project is trying to use an understanding of the data to make better decisions about how to select features. With a potential link to Peter's original idea regarding "extracting a narrative from machine learning" as well as a link to idea that "maybe if we perform more intelligent feature engineering we could use simpler models"
				<ul> 
					<li> Wrote a jupyter noteboook exploring the feature extraction pipeline for the depresjon dataset (predicting depression from activity levels) </li>
					<li> Discussed the difficulty in knowing how to slice data, especially when number of subjects is small but number of samples is large </li>
					<li> Found that entropy performs well as an aggregate feature </li>
					<li> mini literature review of different entropy measures for time series </li>
					<li> started to think about how entropy measures are not robust to noise as they rely on extracting templates from the sample and dont account for dependence between templates </li>
					<li> started to play around with the idea of "how can we extract independent samples from time series data and use these to improve existing entropy measures" </li>
					<li> implemented an entropy measure that uses the matrix profile of a time series and then computes the entropy over the matrix profile </li>
					<li> need to run some proper tests on this new measure. Want to relate it back to how different entropy measures perform according to the shape of the time series </li>
					<li> Think that representation learning for time series data could be really interesting here </li> 
				</ul> 
			</li>
			<li> <b> Research Project 2: Generative Models for Post-Hoc interpretability </b>
				The basic idea behind this project is looking at whether it makes sense to create explanations for the outputs of machine learning models without understanding the input (explaining the data). 
				<ul>
					<li> The paper peter sent me regarding kernels and distance metrics sparked this way of thinking - how do you define "local" in high dimensional space and how important is the choice of kernel. </li>
					<li> Made a jupyter notebook that looks at some of the weknesses of LIME, particularly the issues with sampling and locality </li>
					<li> Currently Lime samples using a normal sampler for the associated bin of the discretised value of each feature in the instance wanting to be explained </li>
					<li> I want to build a generative model of the training data (I was thinking a Guassian Mixture model), sample from that and then use a Fisher kernel to measure locality and explore whether that offers more robust explanations </li>
			</li>
			<li> <b> Research Project 3: Causal Structure of Data for Intepretable Models </b>
				This project questions whether we can have explainability without an understanding of the causal structure of the underlying data. 
				<ul> 
					<li> Made a Jupyter notebook that creates synthetic datasets representing different causally related features and exploring how SHAP attributes feature importance. Results show that SHAP attrbutes importance depdnding on the specific type of causal relation. </li>
					<li> A recent paper has attempted to re-write SHAP to account for causal structure by allowing the symmetric property to be relaxed. I think that this could be improved by identifying the type of causal relation between feature through causal discovery algorithm. This is what I'm going to explore next. </li>
				</ul>
			</li>
			<li> <b> Research Project 4: Bridging Machine Learning and Symbolic Reasoning for Intepretable Models of Noisy Biomedical Data </b>
			This is probobaly my most ambitious of projects and is still being thought out in my head. I was really interested in a paper ("Bridging machine learning and logical reasoning by abductive learning.") that uses abduction with machine learning to learn rules. Im really interested in applying this to see how a discrete module could be bridged with a differntiable learning module to learn explanatory concepts in the data. I think this could actually be interesting in biomedical data - especially as a solution to limited size training sets. 
			</li>
		</ul>
	</li>
</ul>



## PhD Tracking Previous Supervisions 

### Supervision 11/06/2020

#### Discussion Points 

What I’ve been working on: “Extracting Meaning from Biomedical Data”
<ul>
<li> Discussed the “the myth of the accuracy vs. interpretability trade off” as presented by Rudin </li>
<li> Discussed the machine learning development pipeline and where explainability can augment this process.
	<ul>
   <li> Lots of research has been conducted in post-hoc explanations of machine learning models </li>
   <li> Growing research area looks at developing explainability of model training, using influence functions etc </li>
    <li> Lack of literature looking at the explainability of data. This can be further explored by differentiating between ‘explanation’ of the data and how this contributes to an ‘understanding’ of the data and what is meant by these terms. Also discussed the difference between a ‘description’ of the data i.e. summary statistics and more in depth knowledge extraction i.e what sort of distribution is the data drawn form. Overall idea here would be to look at how an explanation/understanding of the data would contribute to the machine learning pipeline and would perhaps address problems including choosing a model based on lack of understanding/ease of use </ul> </li>
<li> Presented the idea of ‘interpretable feature extraction’ and currently researching representation learning. Discussed the question of whether sparsity necessarily implies interpretability. Discussed a link to Kacper’s work on how representation learning is achieved via surrogate models. </li>
<li> Discussed entropy in light of presentation Torty had done that week to Alan Wilson: this involved deriving relative entropy from a bayesian perspective and relating this to entropy maximisation. Discussed the ubiquity of entropy: physical meaning, information theoretic meaning and a probabilistic meaning. Discussed link to scoring methods and how assumptions are encoded in choice of entropy. (Peter to send papers) Discussed the tendency to rely on the KL divergence without explicitly stating assumptions. Discussed how this is due to lack of general understanding/conceptualisation of entropy and could benefit from some bottom up discussion of entropy (machine learning 101). Could also link this back to understanding the data. </li>
<li> Discussed the general problems with trying to conduct work in an oversaturated field positives and negatives to this. Discussed trying to sample ‘locally’ in high dimensions and how this breaks down. Discussed how dimensionality reduction should be performed before neighbours are samples. Discussed the importance of distance metric in high dimensional spaces. Going to investigate how distance metrics affect the predictions from LIME - could I use BLIimey for this? Link to work that Peter had conducted on distance metrics, using Haskell (Peter to send paper) to define distances between different structures i.e. lists and vectors. </li>
<li> Discussed uk Biobank - agreed that I would hold off applying to a particular project until I’ve sandboxed successfully some ideas </li>
<li> Discussed the data I have been sandboxing recently: this is longitudinal data: 1) predicting epileptic fits from brain signals 2) predicting depression from activity data </li>
<li> Discussed ‘extracting meaning from longitudinal data’ this could either be state based models, or sliding windows, or very simple point based models where window size = 1. Can we say, after seeing the data whether we need to model with state based models or with sliding windows? (Peter to send papers, Neil twiney?) Can I link this back to the work I have done? </li>
<li> Discussed also the difficulty in biomedical longitudinal data for diseases looking specifically at the limited subjects but high number of samples and how this affects feature extraction - can we make best guesses about the type of prediction algorithm/features we could use after seeing the shape of the data? Discussed hierarchical modelling as a way to do this. Possible link back to work I did on modelling moral judgments and hierarchically clustering peoples morals and how bias is instilled here. Also discussed how choice of features and algorithm is not just affected by an understanding of the data but also on an understanding of the machine learning/statistical task </li>
<li> Discussed causal inference and relevance to my work. Discussed my ongoing project investigating how current explainability methods/ vanilla regression deal with different types of confounding. This is what you should prepare a presentation on for peter’s group. Also discussed my side project of developing interactive learning resources for causal inference </li>
<li> Discussed potentially getting more involved in FAT - forensics, need to ask Kacper what he wants done to the project and possibly coordinate with miquel. </li>
<li> Discussed Mihaela van der schar, potentially link up but would prefer to do this later on in the project when I have achieved something lol </li>
</ul>


#### Action Points: 
<ul>
<li> Organise and share supervision meeting notes and progress reports - GitHub </li>
<li> Develop GitHub further, by next meeting want to have dedicated ‘research projects’ pages relating to the above directions. </li> </ul>

_________________________________________________


### Supervision 29/04/2020

Discussed <ul>
<li> Peter had reviewed my research proposal and fed back that it looked good but neeeded more of an overall aim - we discussed that this could be health </li>
<li> Peter reccomended contacts from bristol who do health research including Louise millard, biobank </li>
<li> Peter had sorted me a second supervisor, Ollie ray </li>
<li> Discussed covid and also that I am going to stay in London for at least another year </li> </ul>

Actions:
<ul> <li> Contact Louise Millard </li>
	<li> apply to Biobank </li>
	<li> Re-write research proposal to include health ideas - starrt working on stage 1: "extracting meaning form biomedical data </li>
	<li> Prepare and present phd proposal to Bristol Turing working group </li>
	<li> Prepare and present to Alan Wilson's mentoship group with the Turing </li> </ul>



_________________________________________________


### Supervision 17/02/2020 (Bristol)

I didnt actually record properly this meeting which is why this is so vague


Discussed: 
<ul> <li> I am currently wiritng a research proposal </li>

Action Points:
<ul> <li> Continue writing research proposal </li>

_________________________________________________

### Supervision 16/01/2020 (London)

Discussed:
<ul> <li> Peter had reviewed my literature review over christmas, gave feedback, not worth making it into anything formal (too reliant on other pieces of literature, specifically tim miller) but a good source of raw material </li> 
	<li> Good to spend this time thinking about what im actually interested in, discussed a few ideas, decided that I am really interested in the cross over with social sciences but want to keep it machine learning focused (also interested in symbolic AI) not bothered about any particular technique. </li>
	<li> I fedback work I'd done on F score </li>
	<li> discussed explana-narratives and Peter reccomend I research genevieve lively narratist in bristol </li>
</ul>

Action points:
<ul>
	<li> Id been working on some research questions but they were very broad so I need to reveiew these and think more clearly about a narrative3 for the phd that interests me. </li> </ul>



_________________________________________________

### Supervision 2/12/2019 (Bristol)

I didnt actually record properly this meeting which is why this is so vague

Discussed: 
<uL> 
	<li> How to write an effective literature review </li>
</uL>

Actions:
<ul> 
	<li> Continue to work on literature review </li>
</ul>


_________________________________________________

### Supervision 25/11/2019 (Skype) 

Discussed: 
<ul> <li> Carry on with reading around explainable AI </li>
	<li> Bit bored of just reading papers so trying to do some regular coding (Hackerank and Kaggle) and trying to engage with Turing as much as possible via training </li>
	<li> Still expressing an interest in explainability of multi agent system (funny that in hindsight, now I know the terminology I am actually interested in the explainability of the integration of multi-modal data and representation learning)
	<li> Went to Turing spark course and software engineering course </li>
	<li> peter reccommended I think about the following: "what does averaging of F-score on the classes mean" and "how to get verbal narratives out of machine learning experiments". </li>
</ul>

Actions: 

<ul> <li> peter reccommended I work on his conjectures from https://aaai.org/ojs/index.php/AAAI/article/view/5055 to see whether I could prove them. I will focus on this until next meeting </li></ul>


_________________________________________________

### Supervision 11/11/2019 (Bristol)
Discussed:

<ul>
	<li> Github community where members can add their areas of expertise
Reproducible research 
reproducible articles: Type of typesetting that accepts all inputs and offers all
outputs </li>
<li> NIPS submit fragile resultsʼ dependence on regularisation settings
Cross validation - should publish what choices made throughout model
creation and evaluation </li>
<li> Argumentation - used to evaluate explanations - possibility of presenting work
back to research group </li>
<li> Jim smith - possibly a cross over - email to keep him in loop
Francesca Toni will be at panel meeting
Conference on decision support and recommender systems
Jonathan Lowry is working on multi agent systems </li> </ul>


Actions:

<ul>
<li> Next meeting via Skype at 11.30 Monday 25th Nov - sort out Skype prior to this
Create an overleaf and map out literature review </li> 
<li> Carry on reading into argumentation focusing on Francesca tonis ideas & j
Lowry </li>
<li> Book onto conference for 21st and 22nd of nov </li>
<li> Look at Jonathon Lowry lecture series </li> </ul>



_________________________________________________


### Supervision: 21/10/2019 (Bristol)

Discussed:

<ul> 
<li> Idea behind explanations for multi component systems </li>
<li> Idea behind ‘background knowledge” for improving classification systems </li>
<li> Peter to be in Japan from 22/10/19 - 07/11/19 </li>
<li> 3 ideas - social media, fairness, explainability. Social media seemed too 
applied, fairness could be interesting particularly different contexts for bias and
methodology order. Continue with explainability, idea of argumentation and
negotiation amongst agents </li>
<li> Have been lent Argumentation book </li>
<li> Literature Review by Christmas on Overleaf </li> </ul>

Actions:
<ul>
<li> Continue with explainable AI </li>
<li> Read book on Argumentation </li>
<li> Think about literature review </li>
<li> Research Turing Way </li>
<li> Find second supervisor </li>
<li> Book train for next meeting in bristol </li>



_________________________________________________


### Supervision 14/10/2019 (Bristol)
General Project Meeting - introduction to Peterʼs research group

#### Actions:
<ul> 
<li> To be added to Slack group </li>
<li> Send Peter email with outlook email address and re-schedule meeting on
Monday </li>
<li> Email Simon by end of week - sort out desk </li>
<li> Read kascperʼs papers. have plan by Monday </li> </ul>

__________________________________________________

### Supervision 30/9/2019 (Bristol)


#### Admin Stuff 

<ul>
<li> -Turing Induction Week </li>
<li> -What to expect from Turing </li>
<li> -How is long distance relationship going to work </li>
<li> when will we have meeting/when will I submit work </li>
<li> -Phd at Bristol -how is it assessed, first year ‘upgradeʼ? </li>
<li> -my paper </li> </ul>

### Content 

present research proposal, different work packages:
<ul>

<li> Collect moral data -research the best way to collect this form of data </li>
<li> Use data to create a hybrid model of automated decision making 
particularly looking at the impact of model assumptions maybe using non 
parametric models as an alternative and how to aggregate individual models of 
moral behaviour </li>

<li> Reducing bias in automated decision making </li>
<li> Transparency in automated decision making particularly looking at 
procedural regularity. </li></ul>

Feedback from the Turing was that they didnʼt know if there was a viable way 
to do the project. the project proposal needs to focus on things that can be 
realistically achieved and the computational methods that will deliver that. Want to keep it grounded in computer science, want to combine it with Peter 
research area.

Present ideas: I want to move away from the idea of automating moral decision making -think 
this is too hard and complicated 
But I have a few ideas:
<ul>
<li> Data collection, how to collect moral data and how to ensure it representative </li>
<li> Modelling morality to learn more about human ethics </li>
<li> Transparent ai -cryptographic </li>
<li> Different areas of automated decision making </li>
<li> Counterfactual fairness, focus on protecting </li>
<li> How can we make models robust to different assumptions, looking at non parametric models </li> 
<li> Human/technology agency tradeoff in automated decision making https:// 
onlinelibrary.wiley.com/doi/full/10.1002/poi3.198 </li>
<li> Probabilistic programming frameworks, pymc3, contributing to open source </li>
<li> Peterʼs project: AI measurement theory Want to read Artificial intelligence with uncertainty </li>

#### Notes from meeting 

##### Admin:

<ul> 
	<li> Phd Contract Costing has gone through from Bristol -Peter to chaser following 
meeting </li>
<li> At Bristol there are usually annual reviews (6 months for CS) </li>
<li> First Year review is particularly important present a literature review and a plan, 
mini Viva and a pass or fail </li>
<li> Need to look for second supervisor/reviewer </li>
<li> Kascper (PhD student under Peter at Bristol) doing similar thing in explainable python 
package for methodology, high quality software, LIME improvements </li> </ul>


##### Project Discussion:

Andrew Charlesworth based at the Bristol Law Faculty presents interesting 
arguments about ethics washing. Peter expresses that a lot of problems within ethics can be solved with proper 
legislation. Stuart Russel recently brought out a new book Human Compatible: AI and the 
Problem of Control 

Limited AV expertise in Bristol. May be easier to focus on building trust in AI, this objective could be easier to 
measure than ethics . At some point will need to link with psychology/user studies. Interesting area to pursue is the idea of narrative machines, reason that we 
trust is built on stories. Interesting area to pursue could be having a dialogue with interactive ai.


#### Actions 
<ul>
<li> Read, explore and branch out </li>
<li> Read Human Compatible: AI and the Problem of Control </li>
<li> Need to create/find a decent application for keeping track of readings and 
ideas </li>

<li> Develop skills </li>
<li> Come up with a 3 month goal </li> 
<li> Come up with a weekly goal </li>
<li> Peter is speaking at event on the 21st and 22nd November on recommender 
systems -book this, may cost money </li>
<li> Next meeting on the 14th October at 9.30 in room 4.01 in Bristol </li>
</ul>

