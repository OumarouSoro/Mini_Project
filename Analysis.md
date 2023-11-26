# Mini project data analysis workflow
## Written by Oumarou Soro and Mike Mugo

# Whole Genome Sequencing of Extended-Spectrum Beta-Lactamase (ESBL)-Producing Escherichia coli Isolated From a Wastewater Treatment Plant in China
   Xiawei Jiang, Xinjie Cui, Hao Xu, Wenhong Liu, Fangfang Tao, Tiejuan Shao, Xiaoping Pan, Beiwen Zheng

   ### Strain Typing
Strain typing refers to the process of characterizing or identifying different strains of a particular organism, such as bacteria, viruses, or fungi. It involves analyzing genetic, biochemical, or other specific features to differentiate between various subtypes or variants within a species.
In microbiology, strain typing is crucial for understanding microbes' diversity and behaviour, especially concerning infectious diseases. The aim of this project is to reproduce the strain typing data analysis of _**Eschericia coli**_ genomes. The bacteria were isolated from wastewater treatment plants in Taizhou, China.
The assembled genome files were downloaded from DDBJ/ENA/GenBank under bioproject `(PRJNA433283)`. The analysis was performed using the command line mlst 2.23.0.
  ### mlst Script
 ` #!/bin/bash`
 
 `#Script written Oumarou Soro`

`#Date: 25 November 2023`
  
 `for i in *.fna
do`

`mlst $i -q | cut -f1,2,3 >> E_coli_Sequence_Types.tsv
echo "You did a perfect job!"
done`

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
    `#!/bin/bash`
    `#Script written Oumarou Soro`

    `#Date: 25 November 2023`

    `#Go to the current directory`

    `cd ./`

    `#Screening for AMR, Virulence genes, and Plasmids`

    `abricate *.fna >> ARG_results.tsv`

    `#After the ARG screening`

    `echo "ARG screening was done successfully!"`

