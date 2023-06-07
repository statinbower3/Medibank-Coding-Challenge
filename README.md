# Medibank-Coding-Challenge - Solution
Sort through a list of files in a folder structure

#!/bin/bash

#Please enter the directory path


echo "Enter directory path:"
read dir_path

#For loop scans through every text file in the directory and gives out the o/p in decending order


for file in $(find $dir_path -type f -name "*.txt")
do
    echo "Words with at least 2 occurrences in $file:"
    grep -oE '\w+' $file | awk '{print tolower($0)}' | sort | uniq -c | awk '$1>1' | sort -nr
done
