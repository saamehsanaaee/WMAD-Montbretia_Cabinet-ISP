# Pre-trained models
Here are `.keras` and `.pth` files for our trained models.

The WMD, our preliminary model with 90% accuracy, is saved as `WMD_model.keras` and WMAD is saved in multiple ways:
- The `WMAD_model_alt_version.pth` is the working model, trained end-to-end. It is the version that generated the predictions you'll see in our publication.
- The `_NotFinal.pth` files come from the `WMAD_GNN_LSTM_original_ver.ipynb` as the model in that notebook was being trained and saved iteratively.

**The final version of the Working Memory Demand (WMD) model is saved as `WMD_model.keras` and the final version of our Working Memory Architecture and Demand (WMAD) model is saved as `WMAD_model_alt_version.pth`!**

So, if you'd like to use our pretrained models, please use these versions.

> [!NOTE]
> In case you want to use our pretrained models (and help the environment with a tiny step):
> You can simply clone or download this file instead of the whole repository. Please refer to this [discussion comment](https://github.com/orgs/community/discussions/102639#discussioncomment-8293210) for instructions on doing so.
>
> Additional information on data preparation specific to the model will be added to the "[Running the notebooks in this repository](https://github.com/saamehsanaaee/WMAD-Montbretia_Cabinet-ISP/tree/main#running-the-notebooks-in-this-repository)" section of the main `README.md`.
