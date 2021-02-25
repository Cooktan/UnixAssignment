### UnixAssignment

# This files contains information regarding the assignment

# Code used to inspect fang_et_al_genotypes.txt 

1. $ head -n 2  fang_et_al_genotypes.txt
 2. $ awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt 
 3. $ cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t 
 4. $ grep "ZMM" fang_et_al_genotypes.txt | cut -f 1-8 | column -t
 5 $ cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t|sort -k1,2
 5. $ cat fang_et_al_genotypes.txt | cut -f 980-986 | column -t|sort -k1,2

## By inspecting the file I learned:

    1. There are 3  header rows
    2. The first three columns contain in the order, ID#, location details, and group
    3.The remaining columns contain SNP data (Nucleotides) 
    4. The file is very messy
 
 ## Code to inspect snp_position.txt

head -n 1 snp_position.txt
head -n 2 snp_position.txt
tail -n 3 snp_position.txt
cat snp_position.txt | cut -f 1-8 | column -t

 # By inspecting the file I learned:
 
    1.There is a header row
    2. The first three columns contain in the order, ID#, CDV Mark ID, and chromosome
    

 Transpose fang_et_al
    awk -f transpose.awk fang_et_al_genotypes.txt > transposed_genotypes.txt

## Sorting
 
 
 head -n1 fang_et_al_genotypes.txt | grep "ZMM"  > ZMMfang.txt
  awk -f transpose.awk ZMMfang.txt | sort -k1,1 > sorted_transposed_genotypes.txt
tail -n +2 snp_position.txt | sort -k1,1 > sortedsnpZMM.txt
join -1 1 -2 1 -t $'\t' sortedsnpZMM.txt sorted_transposed_genotypes.txt >joinedsnppositionandtransposed


   tail -n +4 transposed_genotypes.txt | sort -k1,1 > sortedtransposedgeno.txt
tail -n +2 snp_position.txt | sort -k1,1 > sortedsnpZMM.txt
join -1 1 -2 1 -t $'\t' sortedsnpZMM.txt sortedtransposedgeno.txt >joinedsnppositionandtransposed


$ wc -l sortedtransposedgeno.txt sortedsnpZMM.txt joinedsnppositionandtransposed
      983 sortedtransposedgeno.txt
     983 sortedsnpZMM.txt
     983 joinedsnppositionandtransposed
    2949 total

#Chromosome Fil





  #snp
sort -k1,1 snp_position.txt > sortedsnpZMM.txt
 
cat sortedsnpZMM.txt | cut -f 1-8 | column -t
# Join the sorted snp_position.txt and sorted fang_et_el



 

# From this I learned that this file is very messy
