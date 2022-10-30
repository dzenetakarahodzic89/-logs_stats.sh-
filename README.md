#!/bin/bash
set -e
if [ $# -eq 0 ]; then
    echo "The script is created with two parameters where we use: 1. path to folder containing logs and 
2. term that you search "
    exit 1
fi 
FILE_PATH=$1 
SEARCH=$2
if [ ! -d "$FILE_PATH" ]; then
    echo "$FILE_PATH does not exist."
    exit 1
fi 
cd "$FILE_PATH"

find . -type f | while read -r file;
do 
    echo "File name: $file Size (B) `wc -c $file | awk '{print $1}'` File Size (KB) `du -k $file | cut -f1` Number of lines `wc -l $file | awk '{print $1}'` repeat `grep -h -c "test" "$file"`";
done





