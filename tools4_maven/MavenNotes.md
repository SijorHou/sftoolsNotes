## reference

[Maven菜鸟教程](https://www.runoob.com/maven/maven-tutorial.html)

[Maven官网下载](https://maven.apache.org/download.cgi)

[csdnMaven安装配置教程](https://blog.csdn.net/weixin_46565024/article/details/122758111?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522f8f57b294025438d467942c2c3d00698%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=f8f57b294025438d467942c2c3d00698&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-122758111-null-null.142^v101^pc_search_result_base5&utm_term=maven%E4%B8%8B%E8%BD%BD%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)

[csdn-Maven教程](https://blog.csdn.net/weixin_43477531/article/details/125164271?ops_request_misc=%257B%2522request%255Fid%2522%253A%25226eb1d30c99aa63ec51061e461c77cc44%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=6eb1d30c99aa63ec51061e461c77cc44&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-125164271-null-null.142^v101^pc_search_result_base5&utm_term=maven%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187)

[csdn IDEA 配置Maven教程](https://blog.csdn.net/qq_38190185/article/details/115943152?spm=1001.2014.3001.5501)

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

<div style="text-align:center">
    <img src="/tools4_maven/pics/Maven原理图.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven原理图</p>
</div>

1. **POM（项目对象模型）**
   - **POM.xml**：这是 Maven 项目的核心配置文件。它定义了项目的所有关键信息，包括项目的依赖、插件、构建信息等。每个 Maven 项目都必须包含一个 `pom.xml` 文件。
     - **项目对象模型（POM）**：它是 Maven 的核心，所有构建、依赖管理、插件等操作都依赖于 POM 文件。

2. **依赖管理模型（Dependency）**
   - **依赖管理**：Maven 的强大功能之一就是它的依赖管理模型。项目通常会使用其他库或模块，这些依赖可以通过在 POM 文件中声明，Maven 会自动下载并管理这些依赖。
     - **中央仓库（central）**：Maven 的默认仓库，存放了大量的开源 Java 库。Maven 会从中央仓库中下载依赖。
     - **B2B 仓库和本地仓库**：这些是其他类型的仓库。例如，B2B 仓库可能是企业内部的私有仓库，本地仓库是存储在开发者机器上的缓存，位于 `~/.m2/repository` 路径中。

3. **构建生命周期与阶段（Build Lifecycle & Phases）**
   - **生命周期（Lifecycle）**：Maven 使用生命周期来定义项目的构建过程，生命周期包含多个阶段（Phases）。例如：
     - **clean**：清理上一次构建产生的文件。
     - **compile**：编译项目的源代码。
     - **test**：运行项目的单元测试。
     - **package**：打包项目为 JAR 或 WAR 文件。
     - **install**：将项目包安装到本地仓库。
     - **deploy**：将构建好的项目包上传到远程仓库。
   - **每个生命周期包括多个阶段**，每个阶段执行特定的构建任务。

4. **插件与 Mojo**
   - **插件（Plug-in）**：Maven 插件是用于执行构建生命周期中每个阶段任务的核心工具。每个插件实现了特定的功能，例如编译代码、打包、运行测试等。
   - **Mojo**：Mojo 是 Maven 插件的核心执行单元。每个插件包含一个或多个 Mojo，每个 Mojo 负责执行生命周期中的一个具体任务。例如，编译 Java 代码的插件可以包含多个 Mojo，其中一个 Mojo 执行编译任务，另一个 Mojo 执行测试任务。

5. **文件的生成和管理**
   - **源文件（Source Files）**：项目的源代码文件，通常存放在 `src/main/java` 路径下。
   - **中间产出文件（Intermediate Outputs）**：这些文件是构建过程中生成的临时文件，如编译后的 `.class` 文件，存放在 `target` 目录下。
   - **资源文件（Resources）**：如配置文件、XML 文件等非代码文件，通常存放在 `src/main/resources` 目录。
   - **最终制品（Final Artifacts）**：最终的构建结果，通常是 JAR、WAR 文件，存放在 `target` 目录下。
   - **打包产物（Packaging Artifacts）**：Maven 最终会根据项目的配置将构建成果打包成合适的格式（例如 JAR、WAR 文件），然后根据需求上传到仓库。

***总结：***
- **POM.xml** 是 Maven 项目的核心配置文件，定义了项目的依赖、插件等信息。
- **依赖管理** 通过中央仓库、B2B 仓库等管理项目所需的外部库和组件。
- **构建生命周期** 包含多个阶段，决定了项目的构建流程。
- **插件和 Mojo** 执行各个阶段的任务，通过插件可以自定义构建过程。
- **构建过程中的文件**，包括源代码、资源、编译文件以及最终的产物，都被 Maven 管理和生成。

图中展示的结构为 Maven 提供了一种清晰的、标准化的方式来管理和构建项目，能够使得 Java 项目的开发和构建更加高效和自动化。

### 安装配置

#### 下载安装
***安装***

[Maven官网下载](https://maven.apache.org/download.cgi)
[csdnMaven安装配置教程](https://blog.csdn.net/weixin_46565024/article/details/122758111?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522f8f57b294025438d467942c2c3d00698%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=f8f57b294025438d467942c2c3d00698&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-122758111-null-null.142^v101^pc_search_result_base5&utm_term=maven%E4%B8%8B%E8%BD%BD%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)

选择下载 3.8.8 binary版本，解压后目录内容如下：
<div style="text-align:center">
    <img src="/tools4_maven/pics/Maven文件目录.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven文件目录</p>
</div>

- **bin**: 含有Maven的运行脚本
- boot： 含有 plexus-classworlds 类加载器框架
- **conf**： 含有 Maven 的核心配置文件
- lib： 含有 Maven 运行时所需要的Java类库

***环境变量添加***

    PS：原来Java如果直接添加的路径作为变量，需要改成以 `JAVA_HOME` 形式的

- 在环境变量中先新建变量
    - 变量名为 `JAVA_HOME`, `MAVEN_HOME` 
    - 路径为包含 bin目录的 路径如 `D:\Software\Java\jdk-17`, `D:\Software\Maven`
- `Path`中添加环境变量 `%JAVA_HOME%\bin`, `%MAVEN_HOME%\bin`

#### Maven功能配置

需要修改 `maven/conf/seetings.xml` 配置文件来修改 Maven 的一些默认配置
1. 依赖本地缓存（本地仓库位置）
```xml
  <!-- localRepository
   | The path to the local repository maven will use to store artifacts.
   |
   | Default: ${user.home}/.m2/repository
  <localRepository>/path/to/local/repo</localRepository>
  -->
  <localRepository>D:\maven-repository</localRepository>
```
2. Maven下载镜像（配置国内阿里镜像）
```xml
    <!-- mirror
     | Specifies a repository mirror site to use instead of a given repository. The repository that
     | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
     | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
     |
    <mirror>
      <id>mirrorId</id>
      <mirrorOf>repositoryId</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://my.repository.com/repo/path</url>
    </mirror>
    阿里云Maven的url：
        http://maven.aliyun.com/nexus/content/groups/public/
        http://maven.aliyun.com/nexus/content/repositories/central/
     -->
    
    <mirror>
      <id>alimaven</id>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
      <mirrorOf>central</mirrorOf>
    </mirror>
```
3. Maven选用编译项目的jdk版本
```xml
  <profile>
      <id>jdk-17</id>

      <activation>
        <activeByDefault>true</activeByDefault>
        <jdk>17</jdk>
      </activation>

      <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <maven.compiler.compilerVersion>17</maven.compiler.compilerVersion>
      </properties>
    </profile>
  </profiles>
```


#### IDEA配置Maven

[csdn IDEA 配置Maven教程](https://blog.csdn.net/qq_38190185/article/details/115943152?spm=1001.2014.3001.5501)