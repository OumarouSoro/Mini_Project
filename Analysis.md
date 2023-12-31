 # Mini_project data analysis workflow
 ## Written by Oumarou Soro and Mike Mugo

# Whole Genome Sequencing of Extended-Spectrum Beta-Lactamase (ESBL)-Producing _Escherichia coli_ Isolated From a Wastewater Treatment Plant in China
   Xiawei Jiang, Xinjie Cui, Hao Xu, Wenhong Liu, Fangfang Tao, Tiejuan Shao, Xiaoping Pan, Beiwen Zheng
   
**Citation:** Jiang X, Cui X, Xu H, Liu W, Tao F, Shao T, Pan X and Zheng B (2019) Whole Genome Sequencing of Extended-Spectrum Beta-Lactamase (ESBL)-Producing _Escherichia coli_ Isolated From a Wastewater Treatment Plant in China. Front. Microbiol. 10:1797. [doi: 10.3389/fmicb.2019.01797](https://www.frontiersin.org/articles/10.3389/fmicb.2019.01797/full)

   ### Strain Typing
Strain typing refers to the process of characterizing or identifying different strains of a particular organism, such as bacteria, viruses, or fungi. It involves analyzing genetic, biochemical, or other specific features to differentiate between various subtypes or variants within a species.
In microbiology, strain typing is crucial for understanding microbes' diversity and behaviour, especially concerning infectious diseases. The aim of this project is to reproduce the strain typing data analysis of _**Eschericia coli**_ genomes. The bacteria were isolated from wastewater treatment plants in Taizhou, China.
The assembled genome files were downloaded from DDBJ/ENA/GenBank under bioproject [PRJNA433283](https://www.ncbi.nlm.nih.gov/bioproject/?term=PRJNA433283) in `fna format`. The analysis was performed using the command line mlst 2.23.0.
  ### Script for moving all fna files from different directories to the same directory
```
#!/bin/bash
#Script written by Oumarou Soro and Mike Mugo
#Date: 18 November 2023
cd ./
#Creating a new directory
mkdir mini_project
#Moving files
cd GCF_003000775.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000815.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000835.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000855.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000865.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000895.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000915.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000935.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000945.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000975.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003000995.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001015.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001025.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001055.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001075.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001085.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001115.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001125.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003001155.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
cd -
cd GCF_003064065.1
cp *.fna /home/soro/Assignment/ncbi_dataset/mini_project
echo "Done"
```
  ### mlst Script
```  
#!/bin/bash
script written by Oumarou Soro and Mike Mugo
Date: November 20, 2023  
for i in *.fna
do
mlst $i -q | cut -f1, 2, 3 >> E_coli_Sequence_Types.tsv
echo "You did a perfect job!"
done

```
  ### AMR screening
AMR stands for antimicrobial resistance, a significant global health concern. It refers to the ability of microorganisms (such as bacteria, viruses, parasites, and fungi) to resist the effects of medications designed to kill them or inhibit their growth.
When microbes become resistant to antimicrobial drugs, infections become more difficult to treat, leading to prolonged illness, increased healthcare costs, and higher mortality rates. Overuse and misuse of antimicrobial drugs in both humans and animals, as well as poor infection prevention and control practices, contribute to the development of antimicrobial resistance.
To address this issue, a multidisciplinary approach is required, involving healthcare professionals, policymakers, researchers, veterinarians, and the general public. Strategies to combat AMR include:

1. Promoting appropriate use of antimicrobials: ensuring these drugs are prescribed and used only when necessary, at the right doses, and for the correct duration.

2. Enhancing infection prevention and control: Implementing measures to prevent the spread of infections in healthcare settings, communities, and agriculture

3. Investing in research and development: developing new antimicrobial drugs, diagnostic tools, and alternative treatments to combat resistant infections.

4. Surveillance and monitoring: tracking the spread of resistant microbes and identifying emerging resistance patterns.

5. Education and awareness: educating healthcare professionals, patients, and the public about the importance of using antimicrobials responsibly and understanding the implications of antimicrobial resistance.
   #### Script for AMR screening using abricate 1.0.1
```
 #!/bin/bash
script written by Oumarou Soro and Mike Mugo
Date: 20 November 20, 2023
Go to the current directory
    cd ./
Screening for AMR, Virulence genes, and Plasmids`
  abricate --db plasmidfinder --csv *.fna > plasmids_results.csv
  abricate --db vfdb --csv *.fna > virulence_results.csv
  abricate *.fna --csv > AMR_results.csv
After the ARG screening
echo "ARG screening was done successfully!"

```
[Virulenfinder 2.0](https://cge.food.dtu.dk/services/VirulenceFinder/), [Plasmidfinder 2.0](https://cge.food.dtu.dk/services/PlasmidFinder/), and [ResFinder](http://genepi.food.dtu.dk/resfinder) are some online tools of the Centre for Genetic Epidemiology that serve to determine virulence genes, plasmids, and AMR genes. But for this mini-project, we used the command line for the Antimicrobial Resistance Genes (ARGs) screening.
