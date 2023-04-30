# 🚀乐跑榜单使用教程

查询个人乐跑数据请 [点击此处](https://jinhuaschool.smart-run.cn/h5/student/) 

## 1.安装 Node.js

①前往[此网站](https://nodejs.org/zh-cn/download/)下载安装
②打开Node.js，输入 npm install -g yarn

## 2.下载源码

①下载此页面源代码并解压
②打开cmd，切换到解压的文件目录(D:，cd 文件目录）
③输入 yarn install

## 3.修改数组

①找到 src/app.vue
②找到一个很长的数组叫 idList
③改成自己班级的乐跑号码(乐跑号码可参考[学生名单](https://github.com/Tylerxz/Name))

## 4.打包程序
①输入 yarn serve
②在 localhost:8080 确认
③输入 yarn build
④新建一个文件夹，里面放 main.js 、electron.package.json (重命名为package.json) 和 dist 里面的文件

## 5.构建程序
①将cmd切换到新建的文件夹
②输入 yarn install
③输入 yarn run build
④在 dist 文件夹里找到构建的程序
