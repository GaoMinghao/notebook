### 有什么命令可以查看文件有多少行  
```sh
wc -l filename
```

### 现在有一个 txt 文件，每一行都表示若干个字段，每个字段用 ｜ 分割，我现在需要批量把第三个字段修改成01，有没有什么 Linux 命令可以批量操作  
```sh
awk -F'|' -v OFS='|' '{$3="01"} 1' input.txt \> output.txt
```

### 现在有一个 txt 文件，每一行都表示若干个字段，每个字段用 ｜ 分割，我现在需要批量检测倒数第三个字段是否为3，倒数第一个字段是否为1，然后把所有的产品打印出来，有没有什么 Linux 命令可以批量操作  
```sh
awk -F'|' '$(NF-2) == "3" && $NF == "1"' data.txt
```

### 现在有一个 txt 文件，每一行都表示若干个字段，每个字段用 ｜ 分割。现在有一个列表“a,b,c”,我现在需要批量检测文件中的第一个字段是否在列表中，若在，则把这一行打印出来，有没有什么 Linux 命令可以批量操作  
```sh
awk -F'|' -v list="a,b,c" 'BEGIN{split(list, arr, ","); for(i in arr) map[arr[i]]=1} $1 in map' input.txt
```

### 如何根据关键字删除文件中的某一行，并且把该行后的所有行往前移动一行  
+ 仅仅在屏幕上预览删除后的结果（不修改原文件）  
```sh
sed '/你的关键字/d' filename.txt
```

+ 直接修改原文件（In-place edit）  
```sh
sed -i '/你的关键字/d' filename.txt
```

+ 更安全的方法  
```sh
grep -v "你的关键字" filename.txt \> temp.txt && mv temp.txt filename.txt
```
