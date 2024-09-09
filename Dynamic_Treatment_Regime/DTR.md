# Dynamic Treatment Regime
## Abstract
A dynamic regime consists of actions to control a trajectory of a specific environment. In particularly, this thesis is more interested to apply dynamic regime on biological environments, in particularly patients. Dynamic treatment regime (DTR) is  a generalize personalized medicine to time-varying treatment. By studying algorithms improving DTR, we could propose better treatments, such as reducing the amount of treatment needed or apply an uncommon strategy. This approach
improves the chances of successful treatment while reducing the risk of side effects.
DTR policies involve making decisions under uncertainty, considering the expected outcomes of different treatment options.
## Introduction
Dynamic Treatment Regime is a theme in Personalized medecine, in fact personalized the treatment for each patient can lead a better outcome for patients, with reducing the amount of drugs for instance which can have side effects such as chemotherapy treatments.
An example of successful Dynamic Treatment Regime where authours \cite{zeng2022optimizing} had optimized a treatment regime warfarin anticoagulation for patiehnts after surgical valve replacement, they showed an improvement of a measure of clotting tendency of blood  compared to INR's clinicians. It exists different algorithms to find better dynamic treatment regimes in particularly oncological treatments, the authors used multiple algorithms to opimize treatment regime and showed Deep Reinforcement Learning algorithm suparsses all others algorithms used in fact but the state of the art way of optimizing  is Deep Reinforcement Learning, in fact the process to find a better treatment given a serie of action and observation refers directly to Reinforcement Learning \cite{mcdonald2023computational}, while Deep Reinforcement Learning demonstrates its is superioty for specefic tasks where decision making is needed, for example ALphaZero which surpasses humans on chess, shogi and Go \cite{silver:2018}. But Deep Reinforcement Learning has drawbachs the intensive use of data, the need of simulator if it is need on a new model building new models can be challeging from ODE to ABM the choose of modeling   is wide  but as i have done the authors and many researchers used pre existing data use offline reinforcement learning algorithms, these data comes directly from hospitals.


## Dynamic Treatment Regime a particular sub problem of Reinforcement Learning

In the context of healthcare, Reinforcement Learning (RL) applied to treatment decisions is known as the Dynamic Treatment Regime. RL, a branch of machine learning, aims to determine the best actions based on observations to maximize an expected cumulative reward. In medical treatments, these observations can include vital signs, images, graphs, or tabular data.

A key concept in RL is the policy, which consists of stimulus-response rules mapping each environmental state to a set of potential actions from which the agent can choose. In its simplest form, the policy may be implemented via a lookup table, but more sophisticated implementations require complex computations, such as search algorithms. The policy is critical for determining how the system functions.

The reward signal represents the agent's goal, guiding its actions by providing feedback based on changes in the environment. As the agent interacts with its surroundings and receives rewards, it strives to maximize the cumulative reward over time. This reward system is the primary mechanism for updating the policy: if an action results in a poor reward, the agent may choose a different action in the same situation in future interactions to explore alternative strategies. In general, the reward signal is a stochastic function, dependent on the state of the environment and the agent’s chosen action.

While the reward signal provides immediate feedback on how successful the last action was, it's often more effective to follow strategies that yield greater benefits in the medium to long term. This is where the Value Function comes into play in Reinforcement Learning (RL). It defines "what is good in the long run" by estimating the total rewards the agent is expected to accumulate over time after leaving a particular state. Instead of selecting actions based solely on immediate rewards, the agent chooses those associated with the highest values. Calculating these values is more complex because, unlike rewards, which are received directly from the environment, values must be predicted based on the agent's past experiences with the environment. Efficiently estimating these values is the core challenge of most RL algorithms.

Another key component of an RL system is the Model, which represents how the environment functions. For instance, given a specific state and a chosen action, the model can be used to predict the next state and the associated reward. RL methods that use models to solve problems are referred to as model-based methods. In contrast, model-free methods rely on trial-and-error learning, without the need for an explicit model, to determine the optimal policy.



By applying RL principles to Dynamic Treatment Regimes, treatment plans can be optimized to improve patient outcomes by continuously adjusting based on real-time feedback.


Given an agent based model software ( NetLOGO) & Q-Learning algorithm researchers \cite{jalalimanesh2017simulation} had proposed a new approach, they used Q-Learning to optimize the treatment. The reinforcement learning algorithm has the goal to treat the disease without overusing radiotherapy in order to avoid healthy tissue.
## Offline vs Online
When a simulator is already created:
1. **Online Reinforcement Learning:**
    
    - **Real-Time Interaction:** In online reinforcement learning, the agent actively interacts with the environment in real-time.
    - **Exploration:** The agent explores the environment by taking actions and receiving immediate feedback from the environment.
    - **Sequential Learning:** Learning occurs as the agent makes decisions sequentially, updating its policy or value function based on the observed outcomes.
    - **Dynamic Environment:** The environment is dynamic, and the agent adapts its strategy as it gains more information through interaction.

When there is no simulator and there are already data/ datasets available.
2. **Offline Reinforcement Learning:**
    - **Historical Data:** In offline reinforcement learning, the agent learns from a fixed dataset that was collected beforehand, without further interaction with the environment.
    - **No Real-Time Interaction:** The agent does not actively explore or interact with the environment during the learning phase.
    - **Batch Learning:** Learning occurs using a batch of data, and the dataset remains static throughout the training process.
    - **Limited Exploration:** The agent's knowledge is limited to the experiences contained in the dataset, potentially leading to suboptimal policies if the dataset lacks diversity.


## Different algorithms used in Dynamic Treatment Regime 

It exists different approaches, one approach which is Augmented INverse Probability Weighted Estimators (AIPWE):
AIPWE is an estimator combining regression based estimator and the invers probability weighted estimator.$X$ is the covariate, $A$ set of actions and $Y$ the response. 
The objective is to estimate the potential outcome \( Y^{*}(a) \), 
which represents the outcome that would be observed if a subject were assigned treatment \( a \).
To evaluate the treatment effect, we compare the average outcome when all subjects receive treatment \( a \), 
denoted by \( \mu_{a} = \mathbb{E}(Y^{*}(a)) \).

Our goal is to estimate \( \mu_{a} \) using the observed data \( \{(X_{i}, A_{i}, Y_{i})\}_{i=1}^{n} \), where:
\begin{itemize}
    \item \( X_{i} \) represents covariates,
    \item \( A_{i} \) is the treatment assignment, and
    \item \( Y_{i} \) is the observed outcome for the \( i \)-th subject.
\end{itemize}

```math
\overset{\wedge}\mu^{AIPWE}_{a,n}
 =\frac{1}{n} \sum_{i=1}^n\left(\hat{Q}_n\left(X_i, a\right)\right)+\frac{1}{n} \sum_{i=1}^n \frac{1_{A_i=a}}{\hat{p}_n\left(A_i \mid X_i\right)}\left(Y_i-\hat{Q}_n\left(X_i, a\right)\right)
```

$1_{A_i=a}$ refers to the indicator function if the patient $i$ is part of treatment group a (or not).
$\hat{Q}_n\left(X_i, a\right)$ refers to the estimation of the outcome Y based on X and treatment A for a patient $i$.
$\hat{p}_n\left(A_i \mid X_i\right)$ refers to the probability estimated.
$\hat{Q}$ and $\hat{p}$ are estimated by machine learning algorithms , in particulalrly if there is enough data by deep learning algorithms.
AIPWE is excellent to estimate treatment effects. AIPWE helps to estimate the outcomes under different treatment regimes. 
Given the different formulas introduced, the aim of a treatment is maximizing expected outcome for a patient $i$
$a_{i}^{*} =  \arg\max_{a\in A} (\mathbb{E}[Y^{*}(a)|X_{i}=x])$. Going, further we want to maximize accross all patients :

$\mathbb{E}\left[Y^{*}(A^{*}(X_i))\right] = \frac{1}{n} \sum_{i=1}^{n} \mathbb{E}\left( Y^{*}(A^{*}(X_i)) \mid X_i \right)$
$Y^{*}(a_{i}^{*})$ refers to the best conditional expectation of the outcome for patient $i$.
We can use these formulas to find the best treatment accross different treatments proposed where data is available but this approach requires already proposed treatments and does not allow to optimize a treatment. For extending, this formulation to treatment regime, we need to have $t$ time thus we propose a new formulation :
$\overset{\wedge}\mu^{TAIPWE}_{a_{t},n}
 =\frac{1}{n} \sum_{i=1}^n\left(\hat{Q}_n\left(X_{i,t}, a_{t}\right)\right)+\frac{1}{n} \sum_{i=1}^n \frac{1_{A_{i,t}=a_{t}}}{\hat{p}_n\left(A_{i,t} \mid X_{i,t}\right)}\left(Y_{i,t}-\hat{Q}_n\left(X_{i,t}, a_{t}\right)\right)$
For one patient, the covariate matrix is not the same in fac the covariate matrix can be health parameters such as molecule concentrations.
Thus for each time steps, we would like to choose the best treatment, in our cases we can say there is one treatment with possible actions. In this case, the formula remains the same for example we can say there are three differents actions possible and for each time steps we would like to optimize the treatment not for only one patient for all patients, given there covariates, we would like to optimize the treatment at the end the formula is :
$$


Finish [AIPWE](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6694251/)
Try to speak a little bit about that
Propose Neural AIPWE
To Do [Model based](https://link.springer.com/content/pdf/10.1007/s11432-022-3696-5.pdf)

In the domain of DTR, Researchers have chosen different techniques to find or to estimate better dynamic treatment regime. A pioneer article \cite{robins2008estimation} in the domain of dynamic treatment regime, 
For schizophrenia, researchers has used stastical methods  \cite{shortreed2012estimating} to compare different treatments. Else Researchers used linear regression models to predict the survival benefit of their new schedule. Thanks to this predictive model, they focused on refining radiation schedules for patients \cite{ayala2021optimal}.





## Modeling Cellular Environments

IAgent-Based Modeling (ABM) is a framework where individual agents operate according to predefined rules, making it particularly suitable for fields like sociology and biology, where entities such as cells can be viewed as agents obeying specific behaviors \cite{jalalimanesh2017simulation}. ABM offers a more intuitive way to represent micro-environments compared to traditional methods like Ordinary Differential Equations (ODE) or Partial Differential Equations (PDE), which require more complex mathematical formulations.

As a bottom-up modeling approach, ABM allows agents to interact with their environment and with each other, resulting in the system's overall behavior emerging from these local interactions. In biological contexts, ABM provides a more detailed and natural way to model organisms, with population dynamics emerging from the behavior of individual entities. For example, describing the tumor micro-environment  is more intuitive with ABM than attempting to derive equations governing it. ABM is particularly useful for modeling biological heterogeneity and offers flexibility in adjusting the levels of detail and aggregation.

Complex systems like tumors, which involve numerous interacting entities and processes that drive growth, invasion, and metastasis, are well-suited to ABM [31]. 

Modeling cancer environment \cite{opasic2020cancersim} or also a agent based model coded where rules are frozen, cannot add new rules to specefic rules \cite{lopez2014estimating} used their own cell based agent model for estimating a radiotherapy dose treatment.
GPU PhysiCell \cite{stack2022openacc}, a part of PhysiCell code is in the GPU and the times speed up, is an ongoing project designed to migrate portions of its serial CPU code to run on GPUs using OpenACC.
GPU approaches very promising models, decrease the computionnal time,  that can lead more cells and more nearby to real biological models. Agent Based Models on GPU \cite{richmond2023flame} highly development or Gell \cite{du2023gell} which offered more than 150 speed up compared to PHysiCell mutli core \cite{du2023gell}. However Gell is less versatile and offers less possibility to build relevant biological models but still a good example of optimized software where performance is primordial. While Flame GPU 2 \cite{richmond2023flame}, he is a tradeoff between versatility and rapidity. In micro Biology, researchers mainly use PhysiCell due to the versatility and the easiest way to use it, compared to Gell or FLAMEGPU2, specially FLAMEGPU2 is not focused on micro-biology some researchers use the framework to build cell microenvironments \cite{borau2024agent}, the cell microenvironment proposed has essential processes such as cell-cell interaction, extracellular matrix interactions, species diffusion, vascularization, cell migration and cell cycling. 
PhysiCell offered a no code model creation software called PhysiCell Studio.



## Bibliography
@article{zeng2022optimizing,
  title={Optimizing the dynamic treatment regime of in-hospital warfarin anticoagulation in patients after surgical valve replacement using reinforcement learning},
  author={Zeng, Juntong and Shao, Jianzhun and Lin, Shen and Zhang, Hongchang and Su, Xiaoting and Lian, Xiaocong and Zhao, Yan and Ji, Xiangyang and Zheng, Zhe},
  journal={Journal of the American Medical Informatics Association},
  volume={29},
  number={10},
  pages={1722--1732},
  year={2022},
  publisher={Oxford University Press}
}

@@article{silver:2018,
  author = {David Silver  and Thomas Hubert  and Julian Schrittwieser  and Ioannis Antonoglou  and Matthew Lai  and Arthur Guez  and Marc Lanctot  and Laurent Sifre  and Dharshan Kumaran  and Thore Graepel  and Timothy Lillicrap  and Karen Simonyan  and Demis Hassabis },
  title = {A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play},
  journal = {Science},
  volume = {362},
  number = {6419},
  pages = {1140-1144},
  year = {2018},
  doi = {10.1126/science.aar6404},
  URL = {https://www.science.org/doi/abs/10.1126/science.aar6404},
  eprint = {https://www.science.org/doi/pdf/10.1126/science.aar6404},
  abstract = {Computers can beat humans at increasingly complex games, including chess and Go. However, these programs are typically constructed for a particular game, exploiting its properties, such as the symmetries of the board on which it is played. Silver et al. developed a program called AlphaZero, which taught itself to play Go, chess, and shogi (a Japanese version of chess) (see the Editorial, and the Perspective by Campbell). AlphaZero managed to beat state-of-the-art programs specializing in these three games. The ability of AlphaZero to adapt to various game rules is a notable step toward achieving a general game-playing system. Science, this issue p. 1140; see also pp. 1087 and 1118 AlphaZero teaches itself to play three different board games and beats state-of-the-art programs in each. The game of chess is the longest-studied domain in the history of artificial intelligence. The strongest programs are based on a combination of sophisticated search techniques, domain-specific adaptations, and handcrafted evaluation functions that have been refined by human experts over several decades. By contrast, the AlphaGo Zero program recently achieved superhuman performance in the game of Go by reinforcement learning from self-play. In this paper, we generalize this approach into a single AlphaZero algorithm that can achieve superhuman performance in many challenging games. Starting from random play and given no domain knowledge except the game rules, AlphaZero convincingly defeated a world champion program in the games of chess and shogi (Japanese chess), as well as Go.},
}

@article{mcdonald2023computational,
  title={Computational approaches to modelling and optimizing cancer treatment},
  author={McDonald, Thomas O and Cheng, Yu-Chen and Graser, Christopher and Nicol, Phillip B and Temko, Daniel and Michor, Franziska},
  journal={Nature Reviews Bioengineering},
  volume={1},
  number={10},
  pages={695--711},
  year={2023},
  publisher={Nature Publishing Group UK London}
}

@article{shortreed2012estimating,
  title={Estimating the optimal dynamic antipsychotic treatment regime: evidence from the sequential multiple-assignment randomized Clinical Antipsychotic Trials of Intervention and Effectiveness schizophrenia study},
  author={Shortreed, Susan M and Moodie, Erica EM},
  journal={Journal of the Royal Statistical Society Series C: Applied Statistics},
  volume={61},
  number={4},
  pages={577--599},
  year={2012},
  publisher={Oxford University Press}
}

@article{ayala2021optimal,
  title={Optimal combinations of chemotherapy and radiotherapy in low-grade gliomas: a mathematical approach},
  author={Ayala-Hern{\'a}ndez, Luis E and Gallegos, Armando and Schucht, Philippe and Murek, Michael and P{\'e}rez-Romasanta, Luis and Belmonte-Beitia, Juan and P{\'e}rez-Garc{\'\i}a, V{\'\i}ctor M},
  journal={Journal of personalized medicine},
  volume={11},
  number={10},
  pages={1036},
  year={2021},
  publisher={MDPI}
}

@article{robins2008estimation,
  title={Estimation and extrapolation of optimal treatment and testing strategies},
  author={Robins, James and Orellana, Liliana and Rotnitzky, Andrea},
  journal={Statistics in medicine},
  volume={27},
  number={23},
  pages={4678--4721},
  year={2008},
  publisher={Wiley Online Library}
}

@article{jalalimanesh2017simulation,
  title={Simulation-based optimization of radiotherapy: Agent-based modeling and reinforcement learning},
  author={Jalalimanesh, Ammar and Haghighi, Hamidreza Shahabi and Ahmadi, Abbas and Soltani, Madjid},
  journal={Mathematics and Computers in Simulation},
  volume={133},
  pages={235--248},
  year={2017},
  publisher={Elsevier}
}

@article{opasic2020cancersim,
  title={CancerSim: a cancer simulation package for Python 3},
  author={Opasic, Luka and Scott, Jacob G and Traulsen, Arne and Fortmann-Grote, Carsten},
  journal={Journal of Open Source Software},
  volume={5},
  number={53},
  pages={2436},
  year={2020}
}

@article{lopez2014estimating,
  title={Estimating dose painting effects in radiotherapy: a mathematical model},
  author={L{\'o}pez Alfonso, Juan Carlos and Jagiella, Nick and N{\'u}{\~n}ez, Luis and Herrero, Miguel A and Drasdo, Dirk},
  journal={PloS one},
  volume={9},
  number={2},
  pages={e89380},
  year={2014},
  publisher={Public Library of Science San Francisco, USA}
}

@article{stack2022openacc,
  title={OpenACC acceleration of an agent-based biological simulation framework},
  author={Stack, Matt and Macklin, Paul and Searles, Robert and Chandrasekaran, Sunita},
  journal={Computing in Science \& Engineering},
  volume={24},
  number={5},
  pages={53--63},
  year={2022},
  publisher={IEEE}
}

@article{richmond2023flame,
  title={FLAME GPU 2: A framework for flexible and performant agent based simulation on GPUs},
  author={Richmond, Paul and Chisholm, Robert and Heywood, Peter and Chimeh, Mozhgan Kabiri and Leach, Matthew},
  journal={Software: Practice and Experience},
  volume={53},
  number={8},
  pages={1659--1680},
  year={2023},
  publisher={Wiley Online Library}
}

@article{du2023gell,
  title={Gell: A GPU-powered 3D hybrid simulator for large-scale multicellular system},
  author={Du, Jiayi and Zhou, Yu and Jin, Lihua and Sheng, Ke},
  journal={Plos one},
  volume={18},
  number={7},
  pages={e0288721},
  year={2023},
  publisher={Public Library of Science San Francisco, CA USA}
}

@article{jalalimanesh2017simulation,
  title={Simulation-based optimization of radiotherapy: Agent-based modeling and reinforcement learning},
  author={Jalalimanesh, Ammar and Haghighi, Hamidreza Shahabi and Ahmadi, Abbas and Soltani, Madjid},
  journal={Mathematics and Computers in Simulation},
  volume={133},
  pages={235--248},
  year={2017},
  publisher={Elsevier}
}

@article{borau2024agent,
  title={An agent-based model for cell microenvironment simulation using FLAMEGPU2},
  author={Borau, C and Chisholm, R and Richmond, P and Walker, D},
  journal={Computers in Biology and Medicine},
  volume={179},
  pages={108831},
  year={2024},
  publisher={Elsevier}
}