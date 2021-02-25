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
 
 ###  Using Now
 grep "ZMM" fang_et_al_genotypes.txt > ZMMfang.txt
 head -n1 fang_et_al_genotypes.txt > header
 cat header ZMMfang.txt >headerZMMfang.txt
  awk -f transpose.awk headerZMMfang.txt | tail -n +4 | sort -k1,1 > sorted_transposed_genotypes.txt
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

#Chromosome Files

awk '$3 =1 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r > Chromosome1_ZMM
awk '$3 =2 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r > Chromosome2_ZMM
awk '$3 =3 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome3_ZMM
awk '$3 =4 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r > Chromosome4_ZMM
awk '$3 =5 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome5_ZMM
awk '$3 =6 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome6_ZMM
awk '$3 =7 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome7_ZMM
awk '$3 =8 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome8_ZMM
awk '$3 =9 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome9_ZMM
awk '$3 = 10{print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome10_ZMM

* Since the missing nucleotides are already ? we dont have to do anything
** Inspect to make sure Chr. 1 was really collected $ cut -c 1-100 < Chromosome1_ZMM




