---
title: Display Newly Written Files
subtitle: Create a table showing the time stamp, endpoint hostname, and file name, sorted in reverse chronological order.
tags: [features]
author: john
---


```sql
event_simpleName=*Written
| table timestamp ComputerName TargetFileName
| sort - by timestamp
```

Representative result table:

|  | timestamp | ComputerName | TargetFileName |
|-:|:---------:|:-------------|:---------------|
| 1 | 1601430853996 | yourHost | \Device\HarddiskVolume1\Windows\someFile |
| 2 | 1601430829107 | otherHost | \Device\HarddiskVolume1\Windows\otherSampleFile |