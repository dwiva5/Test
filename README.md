# Welcome to our Rainfall-Runoff repository!

This is a Gitlab repository for the course CEGM2003 Data Science and Artificial Intelligence for Engineers, created by the HBV group.

The project focuses on rainfall-runoff modeling using a LSTM (Long Short-Term Memory) model and aims to address the lack of uncertainty estimations in 
hydrological predictions.


![#](docs/source/_static/img/rainfall_runoff.jpg)

The README is structured as follows:

- What is the project?
- How is the repository organized and where can the necessary files be found?
- Who contributed to the project and what did the workplan look like?

## Rainfall-runoff modeling

While hydrological predictions are fundamental for effective water resource management, the lack of uncertainty estimations poses a significant challenge. 
Existing applications predominantly focus on single point forecasts, overlooking the critical need for estimating the associated confidence levels. This gap in 
uncertainty consideration hinders informed decision-making. Moreover, the absence of dedicated metrics for evaluating uncertainty estimation further creates an issue. 

For this reason a LSTM (Long Short-Term Memory) model was trained based on imported CAMELS data for the United States, specifically for Hydrological Unit 17 
 (HUC 17) which has data for basins in the North-West upper corner of the United States (namely the states Washington, Oregon).
As the LSTM model itself only returns deterministic results (one discharge prediction per timestep), the Monte Carlo Dropout method was used to obtain
an uncertainty estimation. Based on the results of this methods, uncertainty intervals were created and these were evaluated by newly introduced evaluation 
metrics; the PICP (Prediction Interval Coverage Probability) and PINAW (Prediction Interval Normalized Average Width). By computing the uncertainty interval 
of the methods we hope to bridge the gap in knowledge that currently exists due to the fact that only deterministic results are predicted. Furthermore, by 
evaluating these uncertainty estimations and creating the evaluation metrics we try to estimate what indeed is the best way to model rainfall runoff.

Additionally, the result of the ensemble of the predictions was compared to just the deterministic results of the LSTM. And Transfer Learning was used as well
to assess whether the trained model, trained by data from HUC 17, could also make accurate prediction for basins from another HUC.

## Where can the used files be found

#### Data:

- Folder: [Data](../data/)


    The data used for the proejct can be found under the data folder. In this folder CAMELS_US data can be found which
    consists of three main datasets: 
    - the basin_mean_forcing containing all the meteorological time series data
    - usgs_streamflow containing the streamflow data
    - camels_attribute_v2.0 that extracts all the basin attributes.

    This data was imported for both HUC 17 and HUC 18.

#### Models: 

- Folder: [Models](../neuralhydrology/modelzoo/)


    Under the neuralhydrology folder, there is a subfolder called modelzoo. This folder contains a cudalstm.py file that has the coded
    LSTM model stored there as well as a head.py file which contains the coding for the MCD.

#### Notebook + corresponding files:

- Folder: [Notebook](../Project-Run)

    The notebook that was used to actually use the data and models are stored in a notebook file. This serves as the project documentation in which every step taken during the project is showed and explained.
    
    Apart from the notebook file, there are several folders:

    - Configuration files: used for setting the  configurations of training, validation, model, training and data used for each model run.
    - Evaluation model results: stored evaluation results of the base model and MCD model.
    - LSTM model: results for determining the hidden size of the used LSTM model.


#### Evaluation Metrics:

- Folder: [Evaluation Metrics](../neuralhydrology/evaluation/metrics.py)



    Lastly, the introduced evaluation metrics such as the PICP and PINAW can be found here, in which all the metrics for deterministic evaluation can be found as well.


## Contributors

The HBV group members and their contributions are:

- Dwiva Anbiya Taruna   (5849578)
- Konstantina Bourazani (5728347)
- Hang Long             (5743702)
- Thomas Poort          (4715500)

The detailed work plan is available in the project documentation. 

# Appendix

Here the ReadMe file from the original Neuralhydrology Github can be

## Original Repository

As a forked repository from Neuralhydrology gitlab was used for this project the original README file of that repository is included at the end
of this README as an appendix.

![#](docs/source/_static/img/neural-hyd-logo-black.png)

Python library to train neural networks with a strong focus on hydrological applications.

This package has been used extensively in research over the last years and was used in various academic publications. 
The core idea of this package is modularity in all places to allow easy integration of new datasets, new model 
architectures or any training-related aspects (e.g. loss functions, optimizer, regularization). 
One of the core concepts of this code base are configuration files, which let anyone train neural networks without
touching the code itself. The NeuralHydrology package is built on top of the deep learning framework 
[PyTorch](https://pytorch.org/), since it has proven to be the most flexible and useful for research purposes.

We (the AI for Earth Science group at the Institute for Machine Learning, Johannes Kepler University, Linz, Austria) are using
this code in our day-to-day research and will continue to integrate our new research findings into this public repository.

- Documentation: [neuralhydrology.readthedocs.io](https://neuralhydrology.readthedocs.io)
- Research Blog: [neuralhydrology.github.io](https://neuralhydrology.github.io)
- Bug reports/Feature requests [https://github.com/neuralhydrology/neuralhydrology/issues](https://github.com/neuralhydrology/neuralhydrology/issues)

# Cite NeuralHydrology

In case you use NeuralHydrology in your research or work, it would be highly appreciated if you include a reference to our [JOSS paper](https://joss.theoj.org/papers/10.21105/joss.04050#) in any kind of publication.

```bibtex
@article{kratzert2022joss,
  title = {NeuralHydrology --- A Python library for Deep Learning research in hydrology},
  author = {Frederik Kratzert and Martin Gauch and Grey Nearing and Daniel Klotz},
  journal = {Journal of Open Source Software},
  publisher = {The Open Journal},
  year = {2022},
  volume = {7},
  number = {71},
  pages = {4050},
  doi = {10.21105/joss.04050},
  url = {https://doi.org/10.21105/joss.04050},
}
```

# Contact

For questions or comments regarding the usage of this repository, please use the [discussion section](https://github.com/neuralhydrology/neuralhydrology/discussions) on Github. For bug reports and feature requests, please open an [issue](https://github.com/neuralhydrology/neuralhydrology/issues) on GitHub.
In special cases, you can also reach out to us by email: neuralhydrology(at)googlegroups.com
