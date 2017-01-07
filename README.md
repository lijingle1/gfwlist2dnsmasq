gfwlist2dnsmasq
=================
Intro
-----
Just another script to auto-generate dnsmasq ipset rules using gfwlist

__Notification: Need python2, do not use python3__

GFWList is composed by regular expressions, but dnsmasq rules is formed by domain names. So the conversion from GFWList to dnsmasq rule list is not a equivalent conversion. You might need to add extra rules or modify some converted rules.

Using:
-----

Modify gfwlist2dnsmasq.py:

Change this to your canada DNS server IP&port:
```python
mydnsip = '208.67.222.222'
mydnsport = '443'
```

Change this to your ipset name:
```python
ipsetname = 'gfwlist'
```

Path to save you rule file:
```python
rulefile = './dnsmasq_list.conf'
```

Add your own extra domain here. One domain in a line. eg:
```python
EX_DOMAIN=[ \
'.google.com', \
'.google.com.hk', \
'.google.com.tw', \
'.google.com.sg', \
'.google.co.jp', \
'.google.co.kr', \
'.blogspot.com', \
'.blogspot.sg', \
'.blogspot.hk', \
'.blogspot.jp', \
'.blogspot.kr', \
'.gvt1.com', \
'.gvt2.com', \
'.gvt3.com', \
'.1e100.net', \
'.blogspot.tw' \
]
```
Then run gfwlist2dnsmasq.py:
```bash
python gfwlist2dnsmasq.py
```
If you don't want to generate the rules by yourself, you can download the rule file from:

https://github.com/cokebar/gfwlist2dnsmasq/releases

Known bugs:
-----
1. Invalid lines at the beginning of the list (This script only do with domain address, but gfwlist contains IP addresses):
```
server=/.85.17.73.31/127.0.0.1#5353
ipset=/.85.17.73.31/gfwlist
```
How to fix: just delete these lines.
