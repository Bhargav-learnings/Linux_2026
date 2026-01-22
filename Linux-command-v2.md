# Important Linux Commands 



## grep (Search Text)

grep "error" file.log  
→ Searches for the word "error" in a file  

grep -i error file.log  
→ Case-insensitive search  

grep -r error /var/log  
→ Search recursively in all files under directory  

grep -v error file.log  
→ Show lines NOT containing "error"  

grep -n error file.log  
→ Show line numbers where match occurs  

---

## awk (Column & Pattern Processing)

awk '{print $1}' file  
→ Prints first column  

awk '{print $1,$3}' file  
→ Prints first and third columns  

awk '/error/ {print $0}' file  
→ Prints lines matching "error"  

awk '{sum+=$1} END {print sum}' file  
→ Sums values in first column  

awk -F ':' '{print $1}' /etc/passwd  
→ Uses ':' as delimiter and prints username  

---

## sed (Stream Editor – Search & Replace)

sed 's/dev/prod/' file  
→ Replaces first occurrence of dev with prod  

sed 's/dev/prod/g' file  
→ Replaces all occurrences  

sed -i 's/dev/prod/g' file  
→ Replaces and saves changes in file  

sed -n '10,20p' file  
→ Prints lines 10 to 20  

sed '/error/d' file  
→ Deletes lines containing "error"  

---

## vi / vim (Text Editor – MUST KNOW)

vi file  
→ Opens file in vi editor  

i  
→ Insert mode (start typing)  

Esc  
→ Exit insert mode  

:w  
→ Save file  

:q  
→ Quit editor  

:wq  
→ Save and quit  

:q!  
→ Quit without saving  

/dd  
→ Delete current line  

/word  
→ Search for word  

n  
→ Next match  

---

## top (Real-Time System Monitoring)

top  
→ Shows running processes and resource usage  

top -u user  
→ Show processes of specific user  

Press `P`  
→ Sort by CPU usage  

Press `M`  
→ Sort by memory usage  

Press `k`  
→ Kill a process  

Press `q`  
→ Quit top  

---

## htop (Enhanced top – Interactive)

htop  
→ Better interactive process viewer  

F6  
→ Sort processes  

F9  
→ Kill process  

F10  
→ Exit htop  

Arrow keys  
→ Navigate processes  

---

## tail (Log Monitoring)

tail file  
→ Shows last 10 lines  

tail -n 50 file  
→ Shows last 50 lines  

tail -f file  
→ Follow file in real time  

---

## head (File Preview)

head file  
→ Shows first 10 lines  

head -n 20 file  
→ Shows first 20 lines  

---

## cut (Extract Columns)

cut -d ':' -f1 /etc/passwd  
→ Extract first field using ':' delimiter  

---

## sort (Sort Output)

sort file  
→ Sort lines alphabetically  

sort -n file  
→ Numeric sort  

sort -r file  
→ Reverse sort  

---

## uniq (Remove Duplicates)

uniq file  
→ Remove duplicate adjacent lines  

sort file | uniq  
→ Remove duplicates from file  

uniq -c file  
→ Count occurrences  

---

## wc (Word Count)

wc -l file  
→ Count number of lines  

wc -w file  
→ Count words  

wc -c file  
→ Count characters  

---

## find (Search Files)

find /var -name "*.log"  
→ Find files by name  

find / -type f -size +1G  
→ Find files larger than 1GB  

find . -mtime -1  
→ Files modified in last 1 day  

---

## xargs (Build Arguments)

cat file | xargs rm  
→ Delete files listed in file  

---

## ps (Process Info)

ps -ef  
→ Show all processes  

ps aux  
→ Detailed process snapshot  

---

## lsof (Open Files)

lsof -i :8080  
→ Find process using port 8080  

lsof | grep deleted  
→ Find deleted files still in use  

---

## df & du (Disk Usage)

df -h  
→ Disk usage  

df -i  
→ Inode usage  

du -sh dir  
→ Directory size  

---

## ssh (Remote Login)

ssh user@server  
→ Login to remote server  

## Final Takeaway
- grep → search  
- awk → columns  
- sed → replace  
- vi → edit  
- top/htop → monitor  
- find → locate  
- lsof → debug  
