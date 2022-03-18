---
title: Setup
---
Setup Keras kernel in Palmetto's JupyterLab
---

We will use Palmetto cluster for this workshop with Jupyter Lab.

Please follow this guideline to create a new conda environment and install scikit-learn package.
Log into [Clemson's OpenOnDemand](https://openod02.palmetto.clemson.edu/)

<img src="fig/setup/01.png" style="height:400px">

Under `Clusters` select `Palmetto Shell Access`

<img src="fig/setup/02.png" style="height:400px">

Log into the Palmetto Command Line Shell

<img src="fig/setup/03.png" style="height:800px">

Run the following `qsub` command

```bash
$ qsub -I -l select=1:ncpus=8:mem=15gb:chip_type=e5-2680v4,walltime=2:00:00
```

- Depending on cluster availability, you can set chip_type to be `e5-2670v2`, `e5-2680v3`,
`e5-2680v4`, `6148g`, and `6248g`. 
- You can use `whatsfree` and `freeres` to identify an appropriate `chip_type` setting. 

Next, run the following commands. 

```bash
$ module load anaconda3/2021.05-gcc/8.3.1 cuda/11.1.0-gcc/8.4.1 cudnn/8.1.0.77-11.2-linux-x64-gcc/8.4.1
$ conda create -n tf_2.5 python=3.8 -y
$ source activate tf_2.5
$ export PYTHONNOUSERSITE=1
$ pip install tensorflow==2.5 seaborn scikit-learn matplotlib jupyterlab
```

=> Note: while using **skln** conda environment, if we are missing anything, we can always come back and update using **pip install**
or **conda install** method.

Go back to OpenOnDemand Dashboard, under `Interactive Apps` select `Jupyter Notebook`

<img src="fig/setup/04.png" style="height:500px">

Make the selection on the Jupyter Notebook App as follows:

- `Anaconda Version`: `anaconda3/2021.05-gcc/8.3.1`
- `List of modules to be loaded, separate by an empty space`: `cuda/11.1.0-gcc/8.4.1 cudnn/8.1.0.77-11.2-linux-x64-gcc/8.4.1` 
- `Path to Python virtual/conda environment`: `source activate tf_2.5`
- `Notebook Workflow`: `Standard Jupyter Notebook`
- `Number of resource chunks (select)`: `1`
- `CPU cores per chunk (ncpus)`: `8`
- `Amount of memory per chunk (mem)`: `15gb`
- `Interconnect`: `any`
- `Extra PBS resource allocation request`: `:chip_type=e5-268v4`
- `Walltime`: `04:00:00`

Click `Launch`. 

Click `Connect to Jupyter` once the job is ready. 

<img src="fig/setup/05.png" style="height:300px">

Open a new notebook using the default `Python 3` kernel. Test for the valid installation of `tensorflow`. 

<img src="fig/setup/06.png" style="height:250px">


{% include links.md %}

