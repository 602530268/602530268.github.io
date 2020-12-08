# Sublimetext3使用Virtualenv插件

1. 下载插件：shift  + command + P

2. 输入 install package，进入下载搜索列表

3. 输入 virtualenv进行安装

4. 在sublime菜单栏：tools-build system选择python+virtualenv

5. 在sublime菜单栏：project-add folder to project 选中虚拟环境的文件夹根目录

6. 注意要提前进行虚拟环境的创建，还要运行起来：

> . venv/bin/activate //启动环境
>
> deactivate // 关闭环境

当添加了虚拟环境所在的文件夹（5）并且虚拟环境已经运行起来（6）的时候，shift + command + P，输入 Virtualenv:Activate即可