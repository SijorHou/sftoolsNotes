## reference

[Maven菜鸟教程](https://www.runoob.com/maven/maven-tutorial.html)


## Maven Notes
### Basic Introduction

需要了解 Tomcat、Java、Java Web

***应用场景***
- **依赖导入**：工程中导入jar包尝尝需要手动下载并导入项目，还需注意jar包之间的依赖关系。
    - 使用 Maven 可以统一从 Maven 远程仓库下载（允许大规模数量的jar包）
    - 使用 Maven 在项目中通过 Maven的配置文件来引入jar包、管理jar包之间的依赖关系
- **项目构建**：Maven构建可以更好的操作java源文件：
    - 批量编译
    - 组织文件结构
    - 批量复制jar包
    - ...
- 依赖分享、自动部署...

<div style="text-align:center">
    <img src="/tools4_maven/pics/项目构建.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>项目构建脱离IDE需要专门工具</p>
</div>


Maven 就是一个软件，需要掌握的是：安装、配置、基本功能（项目构建、依赖管理）

<div style="text-align:center">
    <img src="/tools4_maven/pics/Maven功能.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven功能</p>
</div>