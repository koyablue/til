# tree: ignore directories with patterns

https://zaiste.net/posts/tree-ignore-directories-patterns/

- Single directory
```
tree -I node_modules
```

- Multiple directories
```
tree -I 'node_modules|cache|test_*'
```
