# Girape
Graph Isotropic Recursive Column Neural Architecture With Patch Embedding for Multimodal Learning

Experiments conducted on Monastreda: 9 Modalities Dataset for Device State Recognition

# Setup
1. Create Conda environment:
```
conda create -n girape python=3.10
conda activate girape
```
2. Install PyTorch version that suits your system
3. Install requirements
```
pip install -r requirements.txt
```

# Nonastreda
## Dataset
Download the Nonastreda dataset.
All of the Nonastreda experiments are done in Tensorflow except for Minapa_Nona_DFG and Siren_Nona_DFG experiments.

Example: ```experiments/minape_nona/base_10/tool/main.py```

Load Dataset for Tensorflow:
```python
import sys
sys.path.append('/home/<user>/utils')
data_path = 
modality = <path_to_nonastreda>
# random shuffle
modality = ['tool', 'spec', 'scal', 'chip', 'work']
train_ds, test_ds, val_ds, labels_test = get_dataset(data_path, modality)

# Tool=T1 based Dataset: Train:T2-T10, Test: T1
train_ds, test_ds, val_ds, labels_test = get_dataset(data_path, modality, 'T1')

```
Example: ```experiments/minape_nona_dfg/run_training.py```

Load Dataset for PyTorch:
```python
from nonastreda import get_dataset
modalities = ['tool', 'spec', 'scal', 'chip', 'work']

# random shuffle
train_ds, test_ds, val_ds = get_dataset(modalities=modalities)

# Tool=T1 based dataset: Train:T2-T10, Test:T1
train_ds, test_ds, val_ds = get_dataset(modalities=modalities, tool='T1')
```

## Run Experiments
Most of the Nonastreda experiments contain a ```main.py``` file that runs the experiment:
```python
python main.py
```