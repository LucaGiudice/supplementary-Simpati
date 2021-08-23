# Simpati: Repository of Supplementary data and methods

## CONTENT
- Data and methods to replicate the results obtained by Simpati, netDx and PASNet

## REQUIREMENTS
1. Install Docker for your operating system following the [link]()
2. Pull two containers (one containing netDx enviroment, one PASNet enviroment): lgiudice/comp1:latest and lgiudice/comp2:latest
   - In case of a linux operating system you can use the following commands: 
   '''
   docker pull lgiudice/comp1:latest
   docker pull lgiudice/comp2:latest
   '''

### WORKFLOW TO GET netDx RESULTS AND PERFORMANCES ON SOMATIC MUTATION DATA
1. Download and unzip the netDx data and scripts from the [link]()
2. netDx/output directory contains the results used in the publication, if you want to get fresh new output data you can remove everything except: op2_TCGA4netDx_mut
3. Run the comp1 container building the unzipped netDx directory to the following path: /home/lgiudice/containers/netDx_Mut
   - For example: docker run --rm -it -v /netDx_Mut:/home/lgiudice/containers/netDx_Mut lgiudice/comp1:latest /bin/bash
4. Modify the script op3_multi_omics_TCGA.R at the line 101 based on your computational resources, setting the RAM memory and the number of cores
5. Modify the script op3_multi_omics_TCGA_large.R at the line 101 based on your computational resources, setting the RAM memory and the number of cores
6. Now you are ready to run netDx:
   '''
   Rscript op3_multi_omics_TCGA.R
   Rscript op3_multi_omics_TCGA_large.R
   '''

### WORKFLOW TO GET netDx RESULTS AND PERFORMANCES ON RNAseq DATA
1. Download and unzip the netDx data and scripts from the following [link]()
2. netDx/output directory contains the results used in the publication, if you want to get fresh new output data you can remove everything except: op2_TCGA4netDx_RNAseq
3. Run the comp1 container building the unzipped netDx directory to the following path: /home/lgiudice/containers/netDx_RNAseq
   - For example: docker run --rm -it -v /netDx_RNAseq:/home/lgiudice/containers/netDx_RNAseq lgiudice/comp1:latest /bin/bash
4. Modify the script op3_multi_omics_TCGA.R at the line 68 based on your computational resources, setting the RAM memory and the number of cores
5. Modify the script op3_multi_omics_TCGA_large.R at the line 68 based on your computational resources, setting the RAM memory and the number of cores
6. Now you are ready to run netDx
   '''
   Rscript op3_multi_omics_TCGA.R
   Rscript op3_multi_omics_TCGA_large.R
   '''


### WORKFLOW TO GET PASNet RESULTS AND PERFORMANCES ON RNAseq DATA
1. Download and unzip the PASNet data and scripts from the following [link]()
2. PASNet/output/<dataset>/output_py directory contains the results used in the publication for a specific dataset, if you want to get fresh new output data you can delete that directory
3. Run the comp2 container building the unzipped PASNet directory to the following path: /home/PASNet
   - For example: docker run --rm -it -v /PASNet:/home/PASNet lgiudice/comp2:latest /bin/bash
4. Now you are ready to run PASNet workflow: first you will tune the model and then run the model with the tuned parameters
   '''
   python op1_Run_EmpiricalSearch
   python op2_Run
   '''

### Links to the original softwares
- [netDx]()
- [PASNet]()

