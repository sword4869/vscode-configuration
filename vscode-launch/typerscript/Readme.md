# tsconfig.json
```bash
ts --init
```
自动生成tsconfig.json，可以去调整。

```json
{
  "compilerOptions": {
    /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */
    "target": "es2016",
    /* Specify what module code is generated. */
    "module": "commonjs",
    /* Specify the root folder within your source files. */
    // "rootDir": "./",
    /* Specify an output folder for all emitted files. 输出的JavaScript文件所在的文件夹 */
    "outDir": "out",
    /* Enable all strict type-checking options. */
    "strict": true,
    /* Create source map files for emitted JavaScript files. 为了保持源文件和编译后文件之间的联系，设置为true可以通过.ts文件进行调试，方便使用*/
    "sourceMap": true,
  }
}
```

# 编译ts文件成js文件
然后，写个`hello.ts`。

Ctrl+Shift+B 会根据默认的tasks.json编译（没啥好调整的），选择`task:build -tsconfig.json`，就会生成`hello.js`。

```json
{
    // 这就是默认的tasks.json，都挺好的，如果没有更改的必要，那么就不用特意创建写出来.vscode的tasks.json
    "version": "2.0.0",
    "tasks": [
        {
            "type": "typescript",
            "tsconfig": "tsconfig.json",
            "problemMatcher": [
                "$tsc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```

这个tasks其实运行的是`tsc -p ./tsconfig.json`的命令。
```bash
# Compiles the TypeScript project located at the specified path. 
# --project, -p  Compile the project given the path 
# to its configuration file, or to a folder with a 'tsconfig.json'.  

# 这样指定出来就可以起别的名字，比如，tsc -p ./mytsconfig.json
tsc -p tsconfig.json的路径

# 且名字必须是默认的tsconfig.json，比如，tsc -p .
tsc -p 包含tsconfig.json的文件夹
```
# 运行js文件

编译完成后，选择编译出来的`hello.js`，启动调试用默认的`Node.js`。
```bash
E:\MyHacker\nodejs\node.exe .\out\hello.js
Hello Dave!
```
---

PS：唯一的问题就是说`参数格式不正确 - -Command`：见最上层的Readme.me