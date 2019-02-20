###package.json文件

对于自定义模块，需要package.json文件，用于描述模块。

###好处

    1. 方便将项目中的模块分享给他人，通过npm install将依赖的模块下载；
    2. 方便记录所依赖模块的版本号，避免依赖模块的新版本与项目不兼容，导致运行不了的情况；
    3. 方便通过 npm publish 发布到NPM库，供别人下载使用。

###生成package.json文件

** npm init **

    This utility will walk you through creating a package.json file.
    It only covers the most common items, and tries to guess sensible defaults.

    See `npm help json` for definitive documentation on these fields
    and exactly what they do.

    Use `npm install <pkg>` afterwards to install a package and
    save it as a dependency in the package.json file.

    Press ^C at any time to quit.
    package name: (react-test) react-test  ### 项目名称，必要字段  ###
    version: (1.0.0)                       ### 项目版本号，必要字段  ### 
    description: this is a react test      ### 项目描述   ### 
    entry point: (index.js)                ### 入口文件   ### 
    test command:                          ### 项目启动时的脚本命令  ### 
    git repository:                        ### 如果有git地址，可以将这个项目放到GIT仓库里  ### 
    keywords: react,key                    ### 关键词   ### 
    author: limeigou                       ### 作者    ### 
    license: (ISC)                         ### 发布时需要的证书   ### 

    About to write to /Users/gou/Desktop/gou/react-test/package.json:  ###  生成的package.json预览  ###

    {
    "name": "react-test",
    "version": "1.0.0",
    "description": "this is a react test",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [
        "react",
        "key"
    ],
    "author": "limeigou",
    "license": "ISC"
    }


    Is this OK? (yes) yes    ###   若符合预期，输入yes  ###

###属性说明

    {
    "name": "react-test",                     ### 项目名称，必要字段  ###
    "version": "1.0.0",                       ### 项目版本号，必要字段  ###
    "description": "this is a react test",    ### 项目描述,可无   ###
    "main": "index.js",                       ### 模块的入口，知该载入哪个文件   ###
    "scripts": {                              ### 项目启动时的脚本命令，npm run dev, npm run build  ### 
        "test": "echo \"Error: no test specified\" && exit 1"，
        "build": "webpack",
        "dev": "webpack-dev-server --hot"
    },
    "keywords": [                             ### 关键词,可无  ### 
        "react",
        "key"
    ],
    "author": "limeigou",                     ### 作者,可无   ###
    "license": "ISC"，                        ### 发布时需要的证书   ###
    "devDependencies": {                      ### 生产环境下，依赖的模块   ###
        "webpack": "^4.29.5",
        "webpack-dev-server": "^3.1.14"
    }，
    "dependencies": {                        ### 开发环境下，依赖的模块   ###
        "react": "^15.6.2",
        "react-dom": "^15.6.2"
    }
    }