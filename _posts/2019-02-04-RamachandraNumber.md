---
title: "Dihedral Transfrmation from 2D plot to Numbers"
date: 2019-02-04
tags: [Proteins, Structure, Python]
header:
    #image: "/assets/images/post/2019-02-04-RN1.png"
excerpt: "Phi-Psi in One number"

---

Proteins are central to survival of cell. These molecules are result of unique combination of mainly 20 bio-physically 
different amino acids (mostly L-form). Proteins are considered as structural and functional entity of cell, hence its understanding
remains critical to decipher the complex physiological behaviour of life forms.

Use of mapping dihedral angles in a 2D plane has been in the field from early 60s'. 
The celebrated work of G.N. Ramachandran, C. Ramakrishnana nd V. Sasisekharan is considered to be the starting point in protein structure evaluation.
Their findings of different "regions" in Phi-Psi plane, characterise local and non-local behaviour of amino acids in 3D model. Hence, the 
2D plot is paramount to map and understand structural properties of amino acids in a 3D space.

In an attempt to simplifying the 2D representation to 1D numbers, ((Mannige, R. V., Kundu, J., & Whitelam, S. (2016))[http://doi.org/10.1371/journal.pone.0160023]])
have proposed a transformation method. In brief, this method grids the 2D plane and assigns different numbers (0 to 1) for 7 broader
secondary structure regions and disorder regions. 

### Implimentation

A python2.7 implimentation of method above has been done. The codes can be cloned from bitbucket repository 
```
git clone https://taushifkhan@bitbucket.org/taushifkhan/ramanumber.git
```

### Requirements:
* Numpy
* re
* Linux/Unix

### How to use:

1. Via Jupyter-Notebook
    * Install jupyter notebook ```pip install jupyter```
    * Launch  from terminal 
    * open ```DihedralDynamics_proteins.ipynb```

    Files in ```./testFile/``` have some sample dihedral angles used for this analysis.

2. Via Terminal
    ```
    cd ramanumber
    
    [i@u]ramanumber$ python2.7 ramaNumber.py -h
    usage: ramaNumber.py [-h] [-f PHIPSI] [-help HELPDETAIL]
    
    optional arguments:
      -h, --help        show this help message and exit
      -f PHIPSI         phi psi values tab separated
      -help HELPDETAIL  Calculates 1D transformation of 2D Ramachandran plot
    ```
      -- Example
    ```
      pp@linux:rama$ python ramaNumber.py -f ./testFile/GLU_23.xvg
      
      Input: GLU_23.xvg [ 0.51827498 0.49284972 0.50219573 ..., 0.55077455 0.52107648 0.52473937] 
      Transformation saved in GLU_23.xvg_ramaNumber numpy dump 
      
    ```

3. As a module:  call in the class by importing the module
    
    ```python
    import ramaNumber as rN 
    dihedral = Np.loadtxt('./testFile/GLU_23.xvg',dtype='float') 
    R = rN.RamaNumber(dihedral[:,0],dihedral[:,1]) 
    R.getRamaNumber() 
    print R.ramaNumber
    ```



 