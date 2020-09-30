---
title: GeoIP Connections (excluding RFC1918 & loopback)
subtitle: subtitle will go here
tags: [features]
author: john
---


```sql
event_simpleName="NetworkConnectIP4" (RemoteAddressIP4!=192.168.0.0/16 AND RemoteAddressIP4!=10.0.0.0/8 AND RemoteAddressIP4!=172.16.0.0/12 AND RemoteAddressIP4!=127.0.0.0/8)
| dedup RemoteAddressIP4 ComputerName
| iplocation RemoteAddressIP4
| table timestamp ComputerName RemoteAddressIP4 City Country
| sort - by timestamp
```


Representative result table:

|  | timestamp | ComputerName | remoteAddressIP4 | City | Country |
|-:|:---------:|:-------------|:-----------------|:-----|:--------|
| 1 | 1601430853996 | yourHost | 123.123.123.123 | Cheyanne | United States |
| 2 | 1601430829107 | otherHost | 321.321.321.321 | Des Moines | United States |