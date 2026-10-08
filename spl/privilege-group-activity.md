index=your_index sourcetype=WinEventLog:Security EventCode IN (4728,4756)
| sort 0 _time
| streamstats current=f window=1 last(EventCode) as prev_code last(_time) as prev_time
| eval diff=_time-prev_time
| where EventCode=4756 AND prev_code=4728 AND diff<=300

