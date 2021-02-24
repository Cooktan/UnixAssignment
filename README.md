### UnixAssignment
#This files contains information regarding the assignment

##Code used to inspect fang_et_al_genotypes.txt 

head -n 2  fang_et_al_genotypes.txt
 awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt 
 cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t 
 grep "ZMM" fang_et_al_genotypes.txt | cut -f 1-8 | column -t
 cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t|sort -k1,2
 cat fang_et_al_genotypes.txt | cut -f 980-986 | column -t|sort -k1,2

# By inspecting the file I learned:
    #1. There is no header row
    #2. The first three columns contain in the order, ID#, location details, and group
    #3.The remaining columns contain SNP data (Nucleotides) 
    #4. The file is very messy
 
 ## Code to inspect snp_position.txt

head -n 1 snp_position.txt
head -n 2 snp_position.txt
tail -n 3 snp_position.txt
cat snp_position.txt | cut -f 1-8 | column -t

# By inspecting the file I learned:
    #1.There is a header row
    #2. The first three columns contain in the order, ID#, CDV Mark ID, and chromosome
    #3.

 #Transpose fang_et_al
    awk -f transpose.awk fang_et_al_genotypes.txt > transposed_genotypes.txt

## Sorting
  # Fang_et_al
 grep "ZMM" transposed_genotypes.txt | sort > sortedtransposedgeno.txt
  
  #snp
 sort snp_position.txt > sortedsnpZMM.txt
 cat sortedsnpZMM.txt | cut -f 1-8 | column -t



 

# From this I learned that this file is very messy
