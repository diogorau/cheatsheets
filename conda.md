# Conda

## Creating environments
    conda create --name myenv
    conda create -n myenv --prefix ./myenv  # place the environment files in this directory 

## Installing packages before activating
    conda install -n myenv pip
    conda install --prefix ./ibrun pip pandas

## Activating
    conda activate myenv
    conda activate ./myenv

## Installing packages inside the environment
    conda install pandas
    conda install -y ipython  # Answer yes to all questions
    pip install ib_insync

## Updating packages (or python)
    conda update pandas
   
## Deactivating
    conda deactivate

## Removing
    conda remove pandas
    conda remove --name myenv —all

## Viewing environments and packages
    conda env list
<<<<<<< HEAD
    conda env export -n envtest

## Freeing up space
    conda clean --all
=======
    conda info --envs  # Seems to be the same as above
    conda env export -n myenv
    conda env export --no-builds > tobuild.yaml  # create a file to use
    conda list  # Shows all packages, human readable

## Searching for packages
    conda search pandas
>>>>>>> 3cb84d1e7b175f6e372e743e82895b78a25f64ce
