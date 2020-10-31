# Conda

## Creating environments
conda create --name envtest
conda create -n envtest --prefix ./envtest # place the environment files in this directory 

## Installing packages before activating
conda install -n envtest pip
conda install --prefix ./ibrun pip pandas

## Activating
conda activate envtest
conda activate ./envtest

## Installing packages inside the environment
conda install pandas
pip install ib_insync

## Deactivating
conda deactivate

## Removing
conda remove --name envtest —all

## Viewing environments and packages
conda env list
conda env export -n envtest
