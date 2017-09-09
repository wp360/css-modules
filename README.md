# 操作步骤
## 新建项目
1. `npm install -g create-react-app`
2. `create-react-app css-modules --scripts-version custom-react-scripts`
3. `cd css-modules`
4. `code .`
5.  `npm run start` 或者 `yarn start`
## 重点知识
### CSS Modules 用法
[教程参见](http://www.ruanyifeng.com/blog/2016/06/css_modules.html)
```js
按照教程
import React from 'react';
import style from './App.css';

export default () => {
  return (
    <h1 className={style.title}>
      Hello World
    </h1>
  );
};
但是如果你安装的最新版【Webpack】，会有不同，具体参见下面【特别指出】部分，
或参见【custom-react-scripts.md】** Adding a Stylesheet **
```
## **【特别指出】**
## Adding a Stylesheet

This project setup uses [Webpack](https://webpack.github.io/) for handling all assets. Webpack offers a custom way of “extending” the concept of `import` beyond JavaScript. To express that a JavaScript file depends on a CSS file, you need to **import the CSS from the JavaScript file**:

### `Button.css`

```css
.Button {
  padding: 20px;
}
```

### `Button.js`

```js
import React, { Component } from 'react';
import './Button.css'; // Tell Webpack that Button.js uses these styles

class Button extends Component {
  render() {
    // You can use them as regular CSS styles
    return <div className="Button" />;
  }
}
```

**This is not required for React** but many people find this feature convenient. You can read about the benefits of this approach [here](https://medium.com/seek-ui-engineering/block-element-modifying-your-javascript-components-d7f99fcab52b). However you should be aware that this makes your code less portable to other build tools and environments than Webpack.

In development, expressing dependencies this way allows your styles to be reloaded on the fly as you edit them. In production, all CSS files will be concatenated into a single minified `.css` file in the build output.

If you are concerned about using Webpack-specific semantics, you can put all your CSS right into `src/index.css`. It would still be imported from `src/index.js`, but you could always remove that import if you later migrate to a different build tool.

## 开发流程
1. 新建文件：Background（Background.js;Background.css）、Grid(Grid.js;Grid.css;GridItem.js;GridItem.css)、Rocket(Rocket.js;Rocket.css;Smoke.js;Smoke.css)、Title(Title.js;Title.css)
2. 添加对应内容及新增样式
3. 新增素材、调整样式 （Badge.js、Explorer.js、NASA_facts.json）
4. 音频添加
5. 响应式 Media.css
### 具体参见源码

## [**备注**]
1. 问题一：
> 使用Windows `create-react-app css-modules --scripts-version custom-react-scripts` 安装时，可能报错，需要安装开发环境Microsoft Visual Studio。在Mac电脑上也会提醒：‘The xcodeb"command requires the command line developer tools.Would you like to install the tools now?...’如果继续的话，就选择安装Install。当然，如果你一开始就已经安装xcode的话，就不会出现这个。
2. 问题二：
> 一开始的时候，会出现：webpackHotDevClient.js:239 ./src/App.js
  Line 99:  Using target="_blank" without rel="noopener noreferrer" is a security risk: see https://mathiasbynens.github.io/rel-noopener  react/jsx-no-target-blank
解决办法：直接删除target="_blank" 或者 忽略不计。