# Working Memory Architecture and Demand Model
This project is the result of work from the **Montbretia Cabinet** team during the Neuromatch Academy [Computational Neuroscience Course](https://compneuro.neuromatch.io/) and the Neuromatch Academy [Impact Scholars Program](https://impact-scholars.neuromatch.io/).

For information on using this repository, please refer to [this section](https://github.com/saamehsanaaee/WMAD-Montbretia_Cabinet-ISP/tree/main#running-the-notebooks-in-this-repository).

## Project Summary
Working memory (WM) allows us to temporarily hold information “online”, supporting higher cognitive functions such as decision-making, attention, and problem-solving. A key brain region responsible for WM is the prefrontal cortex, an area that differentiates us from other animals. Although our WM resources are limited, it adapts dynamically to the specific demands of different tasks.

Current study uses task-based fMRI data from a large-scale project, the Human Connectome Project, to investigate WM across a range of tasks and conditions. Task-based fMRI measures brain activation during WM tasks, where subjects are asked to recall images presented several trials before.

In our project, statistical and deep learning models acted as “sensors” for task demand and WM activity, predicting how much WM is involved in emotion and language domains. This work provides insights into WM theories from both computational and neurocognitive perspective, with significant implications for education and cognitive rehabilitation.

## Meet the Team!
| Member                | Where could you find them? |
| :-------------------- | :------------------------- |
| Baitong Mu            | [ORCID](https://orcid.org/0009-0008-9040-3108), [GitHub](https://github.com/Mumizz)  |
| Carmen Tang           | [ORCID](https://orcid.org/0009-0005-2491-4987), [GitHub](https://github.com/ckmtang) |
| Zeb Caslick-Waller    | [GitHub](https://github.com/Zebtopia) |
| Wendi Li              | [ORCID](https://orcid.org/0009-0009-0796-1123) |
| Tony Gao              | [ORCID](https://orcid.org/0009-0009-3407-1097) |
| Raúl Rodriguez Cruces | [ORCID](https://orcid.org/0000-0002-2917-1212), [GitHub](https://github.com/rcruces) |
| Saameh Sanaaee        | [ORCID](https://orcid.org/0000-0002-8858-9117), [LinkedIn](https://www.linkedin.com/in/saameh-sanaaee/), [Bluesky](https://bsky.app/profile/saamehsanaaee.bsky.social) |

---
## Data
Main providers of our data have been the Human Connectome Project (HCP), Neuromatch Academy (NMA), and Open Science Framework (OSF).

We are using the HCP data subset that NMA has provided during the NMA Computational Neuroscience (CN) 2024 course. The data is a 100-subject subset of the original HCP young adult, is accessible in [Neuromatch OSF page](https://osf.io/hygbm/), and downloadable through codes provided in the [computational neuroscience course content](https://compneuro.neuromatch.io/projects/fMRI/README.html#:~:text=HCP%20task%20datasets,Murray%2C%20Saad%20Jbabdi) from NMA.

The task-based fMRI data from HCP are time series Blood-oxygen-level-dependent (BOLD) signals that show brain activity through an increased blood flow and oxygenation to the active area of the brain. These signals are organized based on "regions" (see ```regions.npy``` section of the WMD Jupyter Notebook) corresponding to the 360 areas of the Glasser parcellation.

## Running the notebooks in this repository
In terms of reproducitbity, all of our Jupyter Notebooks are self-containing notebooks that you can run independantly of other files.

The best way to run these notebooks would be to use Google Colab since it will give you a quicker data-access time without the hassel of downloading the files directly from OSF.

In addition to this ```README.md```, there are other markdown files provided in our folders that help you navigate the repository.

We should mention that many functions, especially those for setup and data acquisition, were adopted from the NMA-provided notebook (find it in the [Data](https://github.com/saamehsanaaee/WMAD-Montbretia_Cabinet-ISP/tree/main#data) section). Other functions have detailed docstring documentations, providing sufficient information on their use.

> [!NOTE]
> This repository and its documentation will be updated throughout Spring and Summer of 2025 and code snippets for proper use of functions will be added. So, please be patient for the final iterations. For now, the notebooks can just be run from top to bottom as they are so you won't run into any issues if you're looking to use the notebooks.
> There have also been changes in the code and models that will be fully documented in this ```README.md``` file. 
> *In the meantime, please open an issue if you see a giant red flag. We would really appreciate that!*

---
## Models
Two different models were designed.

The Working Memory Demand (WMD) model, a Multilayer Perceptron (MLP), was created during the NMA CN course in the summer of 2024 as our preliminary (or proof of concept) model. Entering the Impact Scholars Program (ISP), we then expanded this model to create an "improved" model, called Working Memory Architecture and Demand (WMAD) model. WMAD is comprised of a pair of parallel models that merge through a fusion layer and are then passed to an MLP (with similar structure to WMD).

These two models give us insight into temporal and spatial activity of working memory and its structure while fulfilling the role of a "task demand sensor".

### WMD (Preliminary) Model
The WMD, constructed with dense and dropout layers that are organized into 4 paired-layers, is a classifier MLP that takes in 360 parcel-based average BOLD signals and generates two outputs. The outputs, probability values corresponding to numbers 0 (low-demand) and 1 (high-demand) act as our labels, telling us how likely it is that the input signal is a 0 or a 1.
### WMAD Model
The WMAD model builds off of the WMD. Main improvements of the WMAD model are use of time series instead of avergae BOLD signals, addition of GNN and LSTM to the model architecture, and higher interpretability of the results due to a more granular output. The output of the GNN-LSTM is similar to the preliminary model, but instead of a single probability value, it generates the probabilities for each of the 360 parcels. With this change, we can identify parcels that contribute the most to WM function. The GNN-LSTM model gives us insight into the spatial architecture of WM.

## Generalization of WMAD
While the results from the WMD gave us valuable insight on how the MLP output could predict WM involvement in other tasks, it did so in a very general way. When we presented emotion and language data to WMD, it predicted the demand of task with 90% accuracy but without much information on the spatial activity.

Although this information on the demand of tasks like "arithmatic problem-solving" or "deriving context of a story" is very much valuable, we need a more quantitative look into these predictions. The GNN-LSTM provides parcel-based predictions that shows which parcels are working in "high-demand" mode. This information, along with the knowledge of "significant parcels of WM function" (derived through model interpretation) can show us how and where WM is involved in other tasks like emotion or language. And these predictions are just the start. HCP alone, provides many more tasks that are beyond intriguing when measured through this WM-involvement lens and that is the next step.

## Acknowledgements
Data were provided in part by the Human Connectome Project, WU-Minn Consortium (Principal Investigators: David Van Essen and Kamil Ugurbil; 1U54MH091657) funded by the 16 NIH Institutes and Centers that support the NIH Blueprint for Neuroscience Research; and by the McDonnell Center for Systems Neuroscience at Washington University.

In addition, we thank Neuromatch Academy (NMA) and the Open Science Framework (OSF) for providing the HCP 100-subject data subset for this project. Finally, we are incredibly grateful for Linzan Liu and Matin Yousefabadi and their support, mentorship, and advice during the NMA CN course during the summer of 2024.
