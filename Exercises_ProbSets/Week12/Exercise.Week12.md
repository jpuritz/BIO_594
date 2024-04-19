# Assignment due on 4/25/2024


## Part 1
In the directory, `/home/BIO594/Exercises/Week_12`, you will find a few useful files and two directories, `realdata` and `simulated`

I would like you to complete the following and push it to your own folder in this repository directory.

* For the simulated data
  * Filter the SNPs (you actually did this last week)
  * Run at least two outlier detection programs
    * Generate a VCF file with only neutral SNPs  
* For the realdata
  * Run BayeScan
  * Run BayEnv
    
Each directory has a `popmap` `environ` and `LibraryInfo` files

`popmap` is a mapping of individuals to populations

`environ` is an environmental factor file for BayEnv

`LibraryInfo` maps samples to sequencing library

There are also PGDspider configuration files and an R file for BayeScan output plotting.


## Part 2

* Repeat the redundancy analysis documented [here](https://github.com/Tom-Jenkins/seascape_rda_tutorial)

**However** Run the analyses in RMarkdown file, knit, and publish to the class Github repository

# Quick tutorial on how to add formatted Rmarkdown output to the github repository

In RStudio (on KITT), I renamed my markdown file from class to `JonsCodeFromClass.Rmd` to make this easier to follow.  You can easily use the "Save As" under the "File Menu" to do this.

Quick Steps:
1. Make sure to knit your file using the <img width="74" alt="image" src="https://github.com/jpuritz/BIO_594/assets/4837703/79f76d7d-abe5-4c22-acbc-ff5d05ca5681"> button or having the <img width="99" alt="image" src="https://github.com/jpuritz/BIO_594/assets/4837703/71308de7-5dd5-4963-86c8-bbba397db649"> checked.
2. Go in to terminal
3. Copy the markdown, Rmarkdown file, and the directory that house images (figures).
```
cp -r ~/JonsCodeFromClass.Rmd ~/JonsCodeFromClass.md ~/JonsCodeFromClass_files ~/repos/BIO_594/Exercises_ProbSets/Week12/
```
The first files is the `.Rmd` or Rmarkdown file, second is `.md` or markdown file, and the third is the file directory `~/JonsCodeFromClass_files`.  The last part of the command is the destination.

4. Now pull, add, commit, and push with git:
```
cd ~/repos/BIO_594/Exercises_ProbSets/Week12/
git pull
git add JonsCodeFromClass*
git commit -a -m "Jon's code from class"
git push
```






### Have fun!


