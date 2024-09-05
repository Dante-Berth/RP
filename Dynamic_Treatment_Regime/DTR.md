# Dynamic Treatment Regime
## Abstract
A dynamic regime consists of actions to control a trajectory of a specific environment. In particularly, this thesis is more interested to apply dynamic regime on biological environments, in particularly patients. Dynamic treatment regime (DTR) is  a generalize personalized medicine to time-varying treatment. By studying algorithms improving DTR, we could propose better treatments, such as reducing the amount of treatment needed or apply an uncommon strategy. This approach
improves the chances of successful treatment while reducing the risk of side effects.
DTR policies involve making decisions under uncertainty, considering the expected outcomes of different treatment options.
## Introduction
Dynamic Treatment Regime is a theme in Personalized medecine, in fact personalized the treatment for each patient can lead a better outcome for patients, with reducing the amount of drugs for instance which can have side effects such as chemotherapy treatments.
An example of successful Dynamic Treatment Regime where authours \cite{zeng2022optimizing} had optimized a treatment regime warfarin anticoagulation for patiehnts after surgical valve replacement, they showed an improvement of a measure of clotting tendency of blood  compared to INR's clinicians. It exists different algorithms to find better dynamic treatment regimes in particularly oncological treatments, the authors used multiple algorithms to opimize treatment regime and showed Deep Reinforcement Learning algorithm suparsses all others algorithms used in fact but the state of the art way of optimizing  is Deep Reinforcement Learning, in fact the process to find a better treatment given a serie of action and observation refers directly to Reinforcement Learning \cite{mcdonald2023computational}, while Deep Reinforcement Learning demonstrates its is superioty for specefic tasks where decision making is needed, for example ALphaZero which surpasses humans on chess, shogi and Go \cite{silver:2018}. But Deep Reinforcement Learning has drawbachs the intensive use of data, the need of simulator if it is need on a new model building new models can be challeging from ODE to ABM the choose of modeling   is wide  but as i have done the authors and many researchers used pre existing data use offline reinforcement learning algorithms, these data comes directly from hospitals.


## Dynamic Treatment Regime a particular sub problem of Reinforcement Learning
Reinforcement Learning and Treatment is called Dynamic Treatment Regime, Reinforcement Learning is a part of machine learning where the objective is given observations to find best actions in order to maximize an expected cumulative reward.  The observation in a treatment can be the vitals

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


## Dynamic Treatment Regime without RL
In the domain of DTR, Researchers have chosen different techniques to find or to estimate better dynamic treatment regime. A pioneer article \cite{robins2008estimation} in the domain of dynamic treatment regime, 
For schizophrenia, researchers has used stastical methods  \cite{shortreed2012estimating} to compare different treatments. Else Researchers used linear regression models to predict the survival benefit of their new schedule. Thanks to this predictive model, they focused on refining radiation schedules for patients \cite{ayala2021optimal}.


## Modeling Cellular Environments

In favor of ABM \cite{jalalimanesh2017simulation}
(Agent-based modeling is among the bottom-up modeling approaches. In this process agents interact with
environment and each other. The overall behavior of the system arises from the collective local behavior of the
involved entities [8]. In agent-based models more detailed description of the organism is required and the population
dynamics may eventually be extracted from the dynamic response of each entity [27]. Agent-based modeling offers a
natural description of a system [4]. For instance, it is more natural to describe how an animal cell migrates in a tissue
than to come up with the equations that rule the dynamics of cellular migration. Moreover, agent-based modeling is a
powerful technique to model biological heterogeneity. It is also a very flexible approach to change levels of description
and aggregation [4]. Tumors are dynamic complex systems wherein several entities, events, and conditions interact
with each other resulting in growth, invasion, and metastases [31]. In this regards, agent-based modeling is an effective
tool to model complex biological phenomena such as tumor growth and cancer therapy. In this research we propose
an agent-based model which can predict the response of vascular solid tumor to irradiation. As declared before, the
agent-based simulation methodology was chosen due to its flexibility for biological modeling and also its power for
modeling heterogeneity)


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