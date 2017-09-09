# 操作步骤
## 新建项目
1. `npm install -g create-react-app`
2. `create-react-app css-modules --scripts-version custom-react-scripts`
3. `cd css-modules`
4. `code .`
5.  `npm run start` 或者 `yarn start`
## 开发流程


## [**备注**]
1. 问题一：
> 使用Windows `create-react-app css-modules --scripts-version custom-react-scripts` 安装时，可能报错，需要安装开发环境Microsoft Visual Studio。在Mac电脑上也会提醒：‘The xcodeb"command requires the command line developer tools.Would you like to install the tools now?...’如果继续的话，就选择安装Install。当然，如果你一开始就已经安装xcode的话，就不会出现这个。
2. 问题二：
> webpackHotDevClient.js:239 ./src/App.js
  Line 99:  Using target="_blank" without rel="noopener noreferrer" is a security risk: see https://mathiasbynens.github.io/rel-noopener  react/jsx-no-target-blank
解决办法：直接删除target="_blank" 或者 忽略不计。