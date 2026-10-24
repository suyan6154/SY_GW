# AGENTS.md

## 项目说明
前端网页设计与开发练习项目，包含多个 HTML/CSS 教学示例。

## 项目结构
- 根目录：按章节编号的 HTML 练习文件（如 1-1.html、10-1.html）
- css.css：全局样式文件
- Images：图片资源目录
- font：iconfont 图标字体目录（iconfont.css 字体方式 / iconfont.js SVG 方式）
- index.html：主入口页面

## 代码规范
- HTML 使用语义化标签
- CSS 遵循现有 css.css 中的命名和组织方式
- 文件命名保持 "章节-序号.html" 格式
- 新建的 HTML 文件需加入超链接到首页 index.html
- 所有变量名称、CSS 类名、ID 名称必须以 `sy_` 开头（如 `sy_title`、`sy-container`）
- 所有 HTML 页面必须在文件头部包含注释：`姓名：苏妍，日期：<当前日期>，功能名称：<页面功能>`
- 每次收到新的用户提示词后，先以追加方式（不覆盖已有内容）写入 `su_prompt.md`，记录内容包括：时间、使用的模型、提示词内容

## 技术栈约束
- 前端使用原生的 HTML、CSS 和 JavaScript 实现
- 图标使用 font 目录下的 iconfont 图标（iconfont.css 字体方式或 iconfont.js SVG 方式）
- 不使用第三方库和 CDN
- 获取服务器端数据使用 fetch

## 注意事项
- 纯静态页面项目，无需构建工具
- 文件中的中文注释和教学内容保持原样
