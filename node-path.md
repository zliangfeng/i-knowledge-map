# Node Path

## path.join

- 很好理解，就是将两个路径拼接起来

```js
path.join('app/libs/oauth', '/../ssl'); // output: app/libs/ssl
```

## path.resolve

- 从左至右，对最后一个绝对路径开始解析

```js
path.resolve('bar', '/foo'); // output: /foo
path.resolve('/bar/bae', '/foo', 'test'); // output: /foo/test
// pwd: /home/mark/project/
path.resolve('test', 'directory', '../back'); // output: /home/mark/project/test/back
```

## __dirname

- `__dirname` is the absolute path to the directory containing the source file
