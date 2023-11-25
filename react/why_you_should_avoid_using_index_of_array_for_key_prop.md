# Why You Should Avoid Using Index Of Array For Key Prop

https://zenn.dev/luvmini511/articles/f7b22d93e9c182

React compares elements by their key props. For example, if there are items A (key='a'), B (key='b'), C (key='c'), and a new element D (key='d') is going to be added, React will compare the current set of items with the new set using keys. In this case, keys a, b, and c will stay the same, and only the item with key='d' will be added. This means that React doesn't need to re-render the first three items; only the new item needs to be rendered.

If the index of an array was used for key prop, unexpected rendering might be happen.
```
const list = ['A', 'B', 'C'];

A(key=0) input: 12345
B(key=1)
C(key=2)

// now a new item D has been added to the place of index=0

D(key=0) input: 12345
A(key=1)
B(key=2)
C(key=3)

// React determined the location of the content of the input by the key, so the content of input'12345' rendered in the wrong place.
```