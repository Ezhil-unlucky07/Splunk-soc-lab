index=* EventCode=1
| search Image="*powershell.exe"
| table _time Computer User ParentImage Image CommandLine
| sort - _time
