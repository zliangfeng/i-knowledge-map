# xargs

## content

```bash
command1 | xargs 
  -t # flag: echo script
  -I {} # placeholder
  -P int # processorNum
  command2 {}
```
