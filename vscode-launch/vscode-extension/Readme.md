没有node_modules时，运行```npm install```，会根据`package.json`来生成node_modules。

`tsconfig.json`是用来编译ts文件，`tsc`编译命令相关。在`package.json`的`"scripts"`有用到。

```json
"scripts": {
    "vscode:prepublish": "npm run compile",
    "compile": "tsc -p ./",
    "lint": "eslint . --ext .ts,.tsx",
    "watch": "tsc -watch -p ./"
},
```