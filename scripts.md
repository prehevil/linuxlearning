# Useful Bash Scripts

## Backup script
```bash
#!/bin/bash
tar -czf backup-$(date +%Y%m%d).tar.gz /home/username/important/
```

## System monitoring
```bash
#!/bin/bash
echo "CPU usage:"
top -bn1 | grep "Cpu(s)"
echo "Memory:"
free -h
echo "Disk:"
df -h /
```
