# backup_microg_lineageos


```
!/bin/bash

export GITHUB_TOKEN=github_pat_11A


myArray=("sailfish" "walleye" "taimen" "blueline" "sargo")
for str in ${myArray[@]}; do
  echo $str
  #github-release release --user $USER --repo backup_microg_lineageos --tag $str



github-release release --user $USER --repo backup_microg_lineageos --tag $str
rm -fr download.lineage.microg.org
wget -r -l1 --no-parent https://download.lineage.microg.org/$str
cd download.lineage.microg.org/$str
for i in `ls line*`
do     
echo $i
github-release upload --user $USER \
   --repo backup_microg_lineageos \
   --tag $str  \
   --name  $i --file  $i
sleep 10
done

done



```
