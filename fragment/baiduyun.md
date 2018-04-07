# 百度云自定义密码

### **按照以下步骤进行操作**

1. 在浏览器中打开百度云盘，选中需要分享的文件，然后点击分享按钮；
2. 点击分享按钮后会弹出一个模态框，先不管它，按 F12 打开开发者工具，切换至控制台（Console），将以下代码复制粘贴到控制台，然后回车

```javascript
javascript:require(["function-widget-1:share/util/shareFriend/createLinkShare.js"]).prototype.makePrivatePassword=function(){return prompt("xxx的自定义百度网盘提取码","xxxx")}
```

3. 然后点击创建私密链接，会弹出输入框，这时输入你想自定义的密码即可！



