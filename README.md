### UnixAssignment
#### Tanner M. Cook
#### Ph.D Student at Iowa State Universty
###### Copyright privileges are owned by Tanner Cook and Iowa State University. For use please contact Tanner Cook (tmcook@iastate.edu)

## This files contains information regarding the assignment

## Code used to inspect fang_et_al_genotypes.txt 

1. $ head -n 2  fang_et_al_genotypes.txt
 2. $ awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt 
 3. $ cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t 
 4. $ grep "ZMM" fang_et_al_genotypes.txt | cut -f 1-8 | column -t
 5 $ cat fang_et_al_genotypes.txt | cut -f 1-8 | column -t|sort -k1,2
 5. $ cat fang_et_al_genotypes.txt | cut -f 980-986 | column -t|sort -k1,2

## By inspecting the fang_et_al_genotypes.txt file I learned:

    1. There are 3  header rows
    2. The first three columns contain in the order, ID#, location details, and group
    3.The remaining columns contain SNP data (Nucleotides) 
    4. The file is very messy
 
 ## Code to inspect snp_position.txt

head -n 1 snp_position.txt
head -n 2 snp_position.txt
tail -n 3 snp_position.txt
cat snp_position.txt | cut -f 1-8 | column -t

 ## By inspecting the file I learned:
 
    1.There is a header row
    2. The first three columns contain in the order, ID#, CDV Mark ID, and chromosome
    

 Transpose fang_et_al
    awk -f transpose.awk fang_et_al_genotypes.txt > transposed_genotypes.txt

### Sorting
 
 
1. grep "ZMM" fang_et_al_genotypes.txt > ZMMfang.txt
2.  head -n1 fang_et_al_genotypes.txt > header
3. cat header ZMMfang.txt >headerZMMfang.txt
4. awk -f transpose.awk headerZMMfang.txt | tail -n +4 | sort -k1,1 > sorted_transposed_genotypes.txt
5. tail -n +2 snp_position.txt | sort -k1,1 > sortedsnpZMM.txt
6. join -1 1 -2 1 -t $'\t' sortedsnpZMM.txt sorted_transposed_genotypes.txt >joinedsnppositionandtransposed


    
#### REDO SORTING!!
## Chromosome Files
# Maize files with ? for missing numbers
1. awk '$3 =1 {print $0}' joinedsnppositionandtransposed | sort -k1,4n  > Chromosome1_ZMM
2. awk '$3 =2 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r > Chromosome2_ZMM
3. awk '$3 =3 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome3_ZMM
4. awk '$3 =4 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r > Chromosome4_ZMM
5. awk '$3 =5 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome5_ZMM
6. awk '$3 =6 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome6_ZMM
7. awk '$3 =7 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome7_ZMM
8. awk '$3 =8 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome8_ZMM
9. awk '$3 =9 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome9_ZMM
10. awk '$3 =10 {print $0}' joinedsnppositionandtransposed | sort -k1,4 -r> Chromosome10_ZMM
*Since the missing nucleotides are already ? we dont have to do anything

~ Just a check: Inspect to make sure Chr. 1 was really collected $ cut -c 1-100 < Chromosome1_ZMM

   Inspect to make sure Chr. 8 was really collected $ cut -c 1-100 < Chromosome8_ZMM

# Maize files with - for missing numbers

1. awk '$3 =1 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4n  > Chromosome1_ZMM-
2. awk '$3 =2 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r > Chromosome2_ZMM-
3. awk '$3 =3 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome3_ZMM-
4. awk '$3 =4 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r > Chromosome4_ZMM-
5. awk '$3 =5 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome5_ZMM-
6. awk '$3 =6 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome6_ZMM-
7. awk '$3 =7 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome7_ZMM-
8. awk '$3 =8 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome8_ZMM-
9. awk '$3 =9 {print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome9_ZMM-
10. awk '$3 = 10{print $0}' joinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome10_ZMM-


cut -c 1-100 < Chromosome1_ZMM-


### Do IT all over again with Teosinte Data


1. grep "ZMP" fang_et_al_genotypes.txt > ZMPfang.txt
2. head -n1 fang_et_al_genotypes.txt > headerZMP
3. cat headerZMP ZMPfang.txt >headerZMPfang.txt
4. awk -f transpose.awk headerZMPfang.txt | tail -n +4 | sort -k1,1 > ZMP_sorted_transposed_genotypes.txt
5. tail -n +2 snp_position.txt | sort -k1,1 > sortedsnpZMP.txt
6. join -1 1 -2 1 -t $'\t' sortedsnpZMP.txt ZMP_sorted_transposed_genotypes.txt >ZMPjoinedsnppositionandtransposed

 $ wc -l sortedsnpZMP.txt ZMP_sorted_transposed_genotypes.txt ZMPjoinedsnppositionandtransposed
    983 sortedsnpZMP.txt
    983 ZMP_sorted_transposed_genotypes.txt
    983 ZMPjoinedsnppositionandtransposed
   2949 total

#### REDO SORTING!!

# Teosinte files with ? for missing numbers
1. awk '$3 =1 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4n  > Chromosome1_ZMP
2. awk '$3 =2 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r > Chromosome2_ZMP
3. awk '$3 =3 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome3_ZMP
4. awk '$3 =4 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r > Chromosome4_ZMP
5. awk '$3 =5 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome5_ZMP
6. awk '$3 =6 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome6_ZMP
7. awk '$3 =7 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome7_ZMP
8. awk '$3 =8 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome8_ZMP
9. awk '$3 =9 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome9_ZMP
10. awk '$3 =10 {print $0}' ZMPjoinedsnppositionandtransposed | sort -k1,4 -r> Chromosome10_ZMP
* Since the missing nucleotides are already ? we dont have to do anything

~ Just a check
*Inspect to make sure Chr. 1 was really collected $ cut -c 1-100 < Chromosome1_ZMP
*Inspect to make sure Chr. 8 was really collected $ cut -c 1-100 < Chromosome8_ZMP

# Maize files with - for missing numbers

1. awk '$3 =1 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4n  > Chromosome1_ZMP-
2. awk '$3 =2 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r > Chromosome2_ZMP-
3. awk '$3 =3 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome3_ZMP-
4. awk '$3 =4 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r > Chromosome4_ZMP-
5. awk '$3 =5 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome5_ZMP-
6. awk '$3 =6 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome6_ZMP-
7. awk '$3 =7 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome7_ZMP-
8. awk '$3 =8 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome8_ZMP-
9. awk '$3 =9 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome9_ZMP-
10. awk '$3 =10 {print $0}' ZMPjoinedsnppositionandtransposed| sed 's/?/-/g' | sort -k1,4 -r> Chromosome10_ZMP-
