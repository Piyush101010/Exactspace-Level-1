# Exactspace-Level-1

Code to truncate the largest file :

largest_log=$(sudo find / -path "/proc/*" -prune -o -path "/run/*" -prune -o -type f -name '*.log' -printf '%s %p\n' | sort -nr | head -1 | cut -d' ' -f2)

largest_log="/var/log/apt/history.log"

echo "Largest log: $largest_log"

# Truncate 
head -n 100 "$largest_log" > tmp_file

# Backup
sudo cp "$largest_log" "${largest_log}.orig" 

# Overwrite with truncated 
sudo mv tmp_file "$largest_log"


echo "Truncated $largest_log to 100 lines"

![Level 1 ss](https://github.com/Piyush101010/Exactspace-Level-1/assets/64955359/2afc4bd9-0e84-4c16-bf40-9eca21abf478)


![level 1 ss 2](https://github.com/Piyush101010/Exactspace-Level-1/assets/64955359/29fe6ad6-601b-428a-b709-60543f6f8e82)
