# Detect File Name Case Changes

Do this.
```
$ git config core.ignorecase false
```

---
If
```
$ git config -l --local | grep core.ignorecase
```
and
```
core.ignorecase=true
```
it means git ignores case changes.
And if
```
core.ignorecase=false
```
it means git detects case changes.

