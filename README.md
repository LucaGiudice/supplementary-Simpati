# Simpati: Repository of Supplementary data and methods

## CONTENT
- Data and methods to replicate the results obtained by Simpati, netDx and PASNet

## REQUIREMENTS
1. Install Docker for your operating system following the [link](https://docs.docker.com/get-docker/)
2. Pull two containers (one containing netDx enviroment, one PASNet enviroment): lgiudice/comp1:latest and lgiudice/comp2:latest
   - With bash: 
   ```
   docker pull lgiudice/comp1:latest
   docker pull lgiudice/comp2:latest
   ```

### WORKFLOW TO GET netDx RESULTS AND PERFORMANCES ON SOMATIC MUTATION DATA
1. Download and unzip the netDx data and scripts from the [link]()
2. netDx/output directory contains the results used in the publication, if you want to get fresh new output data you can remove everything except: op2_TCGA4netDx_mut
3. Run the comp1 container building the unzipped netDx directory to the following path: /home/lgiudice/containers/netDx_Mut
   - With bash: ``` docker run --rm -it -v /netDx_Mut:/home/lgiudice/containers/netDx_Mut lgiudice/comp1:latest /bin/bash ```
4. Modify the script op3_multi_omics_TCGA.R at the line 101 based on your computational resources, setting the RAM memory and the number of cores
5. Modify the script op3_multi_omics_TCGA_large.R at the line 101 based on your computational resources, setting the RAM memory and the number of cores
6. Now you are ready to run netDx:
```
Rscript op3_multi_omics_TCGA.R
Rscript op3_multi_omics_TCGA_large.R
```

### WORKFLOW TO GET netDx RESULTS AND PERFORMANCES ON RNAseq DATA
1. Download and unzip the netDx data and scripts from the following [link](https://univr-my.sharepoint.com/:u:/g/personal/luca_giudice_univr_it/EXaGdLX9_e5Huj_KjoOfF4gB_HcOou9ghoTQ1zF0ZI77zw?e=nslkiE)
   - With bash: ```  wget https://univr-my.sharepoint.com/:u:/g/personal/luca_giudice_univr_it/EXaGdLX9_e5Huj_KjoOfF4gB_HcOou9ghoTQ1zF0ZI77zw?download=1 --no-check-certificate -O netDx.7z ```
3. netDx/output directory contains the results used in the publication, if you want to get fresh new output data you can remove everything except: op2_TCGA4netDx_RNAseq
4. Run the comp1 container building the unzipped netDx directory to the following path: /home/lgiudice/containers/netDx_RNAseq
   - With bash: ``` docker run --rm -it -v /netDx_RNAseq:/home/lgiudice/containers/netDx_RNAseq lgiudice/comp1:latest /bin/bash ```
4. Modify the script op3_multi_omics_TCGA.R at the line 68 based on your computational resources, setting the RAM memory and the number of cores
5. Modify the script op3_multi_omics_TCGA_large.R at the line 68 based on your computational resources, setting the RAM memory and the number of cores
6. Now you are ready to run netDx
```
Rscript op3_multi_omics_TCGA.R
Rscript op3_multi_omics_TCGA_large.R
```


### WORKFLOW TO GET PASNet RESULTS AND PERFORMANCES ON RNAseq DATA
1. Download and unzip the PASNet data and scripts from the following [link]()
2. PASNet/output/<dataset>/output_py directory contains the results used in the publication for a specific dataset, if you want to get fresh new output data you can delete that directory
3. Run the comp2 container building the unzipped PASNet directory to the following path: /home/PASNet
   - With bash: docker run --rm -it -v /PASNet:/home/PASNet lgiudice/comp2:latest /bin/bash
4. Now you are ready to run PASNet workflow: first you will tune the model and then run the model with the tuned parameters
```
python op1_Run_EmpiricalSearch
python op2_Run
```

### Links to the original softwares
- [netDx](https://github.com/BaderLab/netDx/releases)
- [PASNet](https://github.com/DataX-JieHao/PASNet)

