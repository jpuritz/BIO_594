# Take-home Exercise for Week 10

If you're getting an error with `conda`.  Please install miniconda with the following commands:

```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

```
Miniconda3 will now be installed into this location:
/home/maestro/miniconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below
```

Don't worry about the `$PYTHONPATH` warning.

Now run these two commands:
```
~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
```

Press enter and you are good to go.  

Now log out and log back in.  The `conda` command should then work.

### Last Setup Part

```
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda config --set channel_priority strict
conda install mamba
```

## Exercise Part 1

Run the `Ref.Ex` command line tutorial

## Exercise Part 2

### How many loci are there?

I've placed some files in the `/home/BIO594/DATA/Week10/` directory.  They are ddRADseq files that have already been demultiplexed.  

Using your new RADSeq assembly skills:

* Post a markdown document to this directory showing your efforts to answer the question: 
	* How many loci are there in the data set?

* Post a `reference.fasta` file with your assembled reference

* You can use the material from class or anything else you might find at [dDocent.com](https://www.ddocent.com/)
