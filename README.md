# Automatic ECG diagnosis using a deep neural network
## Datech Experiments
As a part of Bigco studio, we have forked this public repository as a reference labeling model for our ECG visualization project.

This model is the one that is published in the Nature aritcle here:
- https://www.nature.com/articles/s41467-020-15432-4

### QuickStart
Clone this repository 
```
git clone https://github.com/Xingyu96/automatic-ecg-diagnosis.git
```

In the root folder, install the packages below (for windows install using conda package manager)
```
numpy>=1.14.3
pandas>=0.22
tensorflow==2.2
h5py>=2.8
xmljson>=0.1.9
scipy>=1.1
scikit-learn>=0.20
tqdm>=4.26
xarray>=0.11.2
seaborn>=0.9
openpyxl>=3.0
```

The pre-trained model is available in `model/model.hdf5` and a test dataset is provided in `data/ecg_tracings.hdf5`. So we have generated a sample test output in the folder `outputs/datech_outputs/test1.npy` by running the following command:
```
python predict.py data/ecg_tracings.hdf5 model/model.hdf5 --ouput_file outputs/datech_outputs/test1.npy 
```

If you wish, you can follow the instructions in the original github Readme (continued below this section) to train your own model as well. However the training datasets are not fully available to the public (but can be requested by contacting the original authors).

### Output
You can use the jupyter notebook `outputs/datech_outputs/test_prediction.ipynb` to examine the output. Currently a few functions in there help visualize and compare the ground truth vs. predictions. In here we also patched in a column to the dataset to identify 'Normal ECG' for convenience. The test sample size is 827. Two example outputs are included below.

![test_sample_2](https://user-images.githubusercontent.com/14202464/163278023-7c629b81-9c84-4b11-bf70-bd16ccf1c275.png)
![test_sample_15](https://user-images.githubusercontent.com/14202464/163278037-bb42b8f4-c47b-4fad-9b89-82cd8e716a06.png)

The labels above are:
```
# 1st degree AV block
# Right bundle branch block
# Left bundle branch block
# Sinus bradycardia
# Atrial fibrillation
# Sinus tachycardia
# Normal
```
It's good that these labels are associated with particular locations on the heart, so we have a working reference model on which we can base our UI design. It's also good that the test accuracy for this model is around 0.97, which is very encouraging. You can examine the details in `outputs/figures` and `outputs/tables`.

### Next Steps
- Adjust our UI based on this prediction model
- Add more models into this working version (requires retraining the model)


### Original Github Readme
- https://github.com/antonior92/automatic-ecg-diagnosis
