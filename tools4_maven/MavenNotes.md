## reference

[Maven菜鸟教程](https://www.runoob.com/maven/maven-tutorial.html)

[Maven官网下载](https://maven.apache.org/download.cgi)

[csdnMaven安装配置教程](https://blog.csdn.net/weixin_46565024/article/details/122758111?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522f8f57b294025438d467942c2c3d00698%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=f8f57b294025438d467942c2c3d00698&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-122758111-null-null.142^v101^pc_search_result_base5&utm_term=maven%E4%B8%8B%E8%BD%BD%E5%AE%89%E8%A3%85%E4%B8%8E%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)

[csdn-Maven教程](https://blog.csdn.net/weixin_43477531/article/details/125164271?ops_request_misc=%257B%2522request%255Fid%2522%253A%25226eb1d30c99aa63ec51061e461c77cc44%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=6eb1d30c99aa63ec51061e461c77cc44&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-125164271-null-null.142^v101^pc_search_result_base5&utm_term=maven%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187)

[csdn IDEA 配置Maven教程](https://blog.csdn.net/qq_38190185/article/details/115943152?spm=1001.2014.3001.5501)

[依赖查询 maven-repository](https://mvnrepository.com/)

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
- 检测 Maven配置成功： cmd 中执行 `mvn -v`

#### Maven功能配置

需要修改 `maven/conf/seetings.xml` 配置文件来修改 Maven 的一些默认配置，***单数标签都放在复数标签之前***
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

<div style="text-align:center">
    <img src="/tools4_maven/pics/IDEA设置Maven.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>IDEA设置Maven</p>
</div>

<div style="text-align:center">
    <img src="/tools4_maven/pics/新项目设置.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>新项目设置</p>
</div>

也可以在IDEA中设置每个新项目都使用Maven

#### GAVP
在 Maven 中，**GAVP** 是用来标识一个 Maven 工程或库的唯一标识符，由四个部分组成，分别是 **G**（Group ID）、**A**（Artifact ID）、**V**（Version） 和 **P**（Packaging）。

1. **GAVP 的组成**

- **G (Group ID)**：表示项目所属的组或组织，通常使用公司或组织的域名反转形式（例如 `com.example`）。***它用于唯一标识一个项目的所有模块或组件***。

- **A (Artifact ID)**：表示项目或库的名称，它是项目的唯一标识符，***通常对应项目的名称或模块名称***。这个 ID 是在同一组（Group ID）下唯一的。

- **V (Version)**：表示项目的版本号，通常遵循语义化版本（Semantic Versioning）规则，如 `1.0.0`、`1.2.3` 等。`主版本号.次版本号.修订版本`

- **P (Packaging)**：表示项目的打包类型，指定项目最终生成的构建产物类型。常见的值有：
  - `jar`：Java ARchive 文件（最常见的格式）
  - `war`：Web ARchive 文件（用于 Web 项目）
  - `pom`：用于 POM 文件本身（通常用于父项目）
  - `ear`：Enterprise ARchive 文件
  - `zip`：压缩包等

2. **GAVP 的作用**

GAVP 在 Maven 中的作用是唯一标识一个构件（Artifact）。每个构件的 GAVP 组合在 Maven 中都是唯一的，这使得 Maven 可以从远程仓库下载、管理和依赖不同版本的库。

例如，在 POM 文件中声明一个依赖时，需要提供该依赖的 GAVP 信息，Maven 就能够根据这些信息从中央仓库（或其他仓库）下载相应的构件。

3. **GAVP 示例**

假设你想在 Maven 项目中引用 Apache Commons Lang 库，相关的 GAVP 信息如下：

```xml
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.12.0</version>
    <packaging>jar</packaging>
</dependency>
```

这里的 GAVP 是：
- **Group ID**：`org.apache.commons`
- **Artifact ID**：`commons-lang3`
- **Version**：`3.12.0`
- **Packaging**：`jar`

4. **为什么使用 GAVP**

- **唯一性**：每个库或项目在 Maven 中都是通过 GAVP 来唯一标识的，因此可以确保不同版本的相同库不发生冲突。
- **依赖管理**：当你在项目的 `pom.xml` 文件中声明依赖时，Maven 会根据 GAVP 信息查找并下载正确的依赖版本。
- **构建过程管理**：Maven 通过 GAVP 来管理项目构建中的各个模块和依赖关系，确保构建过程中的一致性和完整性。

5. **总结**

- **GAVP** 是 Maven 用来唯一标识构件（Artifact）的四个关键属性：Group ID（组织/组标识）、Artifact ID（项目标识）、Version（版本号）和 Packaging（打包类型）。
- 通过 GAVP，Maven 可以精确地查找和管理项目中的依赖，确保构建过程中的一致性、可复现性和模块化管理。

GAVP 模式帮助 Maven 在构建和管理 Java 项目时保持结构清晰、依赖管理方便、版本控制一致。


### 创建 Maven Java工程 

#### 新建 Maven 模块

<div style="text-align:center">
    <img src="/tools4_maven/pics/项目中新建Maven模块.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>项目中新建Maven模块</p>
</div>

- 在当前项目结构中，新建 module
- 设置对应的 GAVP (P 默认就是 jar packaging了)
- 新建使用Maven的module在项目中结构如下

<div style="text-align:center">
    <img src="/tools4_maven/pics/Maven-module.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven-module</p>
</div>



#### 依赖添加

[依赖查询 maven-repository](https://mvnrepository.com/)

<div style="text-align:center">
    <img src="/tools4_maven/pics/maven-repository.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven-repository</p>
</div>

<div style="text-align:center">
    <img src="/tools4_maven/pics/配置依赖.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>配置依赖</p>
</div>

- Maven-repository 中查询 jar 包所需依赖，直接复制配置文件
- 在Maven项目的的 pom.xml 配置文件中添加所需依赖
- IDEA 右侧 Maven管理中，点解循环图标按钮，更新配置


### 创建 Maven Web工程

***先按照前面java工程的Maven创建，在项目新建一个 module，`maven_Web`***

Web 工程和 java工程的区别仅仅在于 ***java工程缺少一个 Web模块***（其中设置着 Web资源的路径），想要将 maven_Web （初创时是一个java工程） 真正变为一个 Web工程：需要在其中加入 Web模块：


<div style="text-align:center">
    <img src="/tools4_maven/pics/Maven构建Web项目1.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>Maven构建Web项目1</p>
</div>

如图所示：
- 直接在 web.xml 文件中添加属性为 `war` 包，然后 maven 刷新重新加载项目
- 然后会出现 默认的web 资源目录
- 根据web 资源目录，上面 + 添加 部署描述符 web.xml
- 最后出现左侧的 webapp下内容，**注意目录安排要根据默认生成的 web资源目录**

### 项目构建
#### 构建命令：编译、清理、测试
<div style="text-align:center">
    <img src="/tools4_maven/pics/lombok-maven导入.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>lombok-maven导入</p>
</div>

***如图所示***
- maven_java 项目中，在 src.main.java 先新建 com.sijor.maven.User Java文件
- 然后在 添加 `lombok.jar` 的依赖 （参考上面创建Maven Java 工程的依赖添加）
- 然后更新 Maven配置
- `lombok.jar` 可以直接导入关联私有属性的构造器、getter、setter等方法，不必再编写
- ***在 maven_java的 命令行中执行编译命令 `mvn compile`***
  - 注意：***`mvn compile` 只能编译项目主文件***
  - 若test目录中的测试文件需要编译，执行命令 `mvn test-compile`
- 执行 `mvn test` 会自动执行测试文件
  - ***测试文件名称必须 以 Test 开头或结尾 如 `xxxTest`***
- 可以一次执行多个命令，按照顺序列出命令，如 `mvn clean test` 会先清理然后测试


只需要在项目的pom文件中声明依赖信息，Maven就会自动解析依赖，根据pom.xml文件下载相关依赖及其传递性依赖（依赖的依赖）

#### 构建命令：打包

首先，理解插件机制： **Maven 的功能主要通过插件来实现，插件是一组可重用的构建逻辑**，观察如下命令所用到的插件，插件的执行都是顺序的


```bash
(base) PS E:\Projs\MyProjs\JavaProj\mave-test\maven_java> mvn compile
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------------< com.sijorhou.maven:maven_java >--------------------
[INFO] Building maven_java 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ maven_java ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 0 resource
[INFO]
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ maven_java ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to E:\Projs\MyProjs\JavaProj\mave-test\maven_java\target\classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.046 s
[INFO] Finished at: 2025-03-15T23:21:30+08:00
[INFO] ------------------------------------------------------------------------

```
同理，有如下插件使用情况：
1. ***打包***
- `mvn compile` 用到的插件
  - `maven-resources-plugin:2.6:resources`
  - `maven-compiler-plugin:3.1:compile`

2. ***清理***
- `mvn clean` 用到的插件
  - `maven-clean-plugin:2.5:clean`

3. ***测试***
- `mvn test-compile` 用到的插件
  - `maven-resources-plugin:2.6:resources`
  - `maven-compiler-plugin:3.1:compile`
  - `maven-resources-plugin:2.6:testResources`
  - `maven-compiler-plugin:3.1:testCompile`
- `mvn test ` 用到的插件
  - 所有`mvn test-compile` 用到的插件
  - `maven-surefire-plugin:2.12.4:test`

4. ***打包***

    1. 执行命令，会将 Java工程打包成 `jar` 包，将Web工程打包成 `war`包

    2. 注意插件版本与jdk不兼容的报错：
    ```bash
    Execution default-war of goal org.apache.maven.plugins:maven-war-plugin:2.2:war fail

    ed: Unable to load the mojo 'war' in the plugin 'org.apache.maven.plugins:maven-war-plugin:2.2' due to an API incompatibility: org.codehaus.plexus.component.repository.exception.ComponentLookupException: Cannot access defaults field of Properties

    ```
    3. 解决版本问题：在 pom.xml 中添加如下内容：
    ```xml
    <build>
        <!-- jdk17 和 war包版本插件不匹配，添加这里的插件配置，然后更新Maven项目 -->
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>3.2.2</version>
            </plugin>
        </plugins>
    </build>
    ```


- `mvn package` 用到的插件
  - `maven-resources-plugin:2.6:resources`
  - `maven-compiler-plugin:3.1:compile`
  - `maven-resources-plugin:2.6:testResources`
  - `maven-compiler-plugin:3.1:testCompile`
  - `maven-surefire-plugin:2.12.4:test`
  - `maven-jar-plugin:2.4:jar`

#### 构建命令：安装

如图所示，**希望 maven-Web 工程能够使用 maven-java 项目，即依赖与 maven-java项目**，已经在 pom.xml 文件中添加了依赖，但是执行 `mvn package` 依然会报错 `Could not find artifact com.sijorhou.maven:maven_java:jar:1.0-SNAPSHOT`

<div style="text-align:center">
    <img src="/tools4_maven/pics/安装命令解决的问题.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>mvn install 解决的问题</p>
</div>

这是因为，Maven解析依赖的时候，会现在本地仓库查找所需依赖，然后再到中央仓库寻找，上述 maven-java项目只是打包生成了 .jar 文件，任何仓库中都不存在该文件，***所以如果想依赖本地.jar包，应该先安装到本地仓库，即 `mvn install`***


- `mvn install` 用到的插件
  - `maven-resources-plugin:2.6:resources`
  - `maven-compiler-plugin:3.1:compile`
  - `maven-resources-plugin:2.6:testResources`
  - `maven-compiler-plugin:3.1:testCompile`
  - `maven-surefire-plugin:2.12.4:test`
  - `maven-install-plugin:2.4:install`


#### IDEA 的可视化操作
前面截图中可以看到，IDEA 中的Maven面板，可以直接执行基本 Maven命令，而无需命令行输入

其中 `Plugins` 是对应命令所需的基本默认依赖，由此可以看出：
***依赖文件主要分为三类***：
  1. 自定义的项目.jar文件作为依赖
  2. 项目中要用到的 .jar包作为依赖
  3. Maven命令执行所需的插件的默认依赖


### 依赖管理

***依赖管理***

Maven 依赖管理是 Maven 软件中最重要的功能之一。使得软件包依赖的管理和使用更加智能和方便，简化了开发过程中的工作，并提高了软件质量和可维护性。

- Maven 的依赖管理能够帮助开发人员**自动解决软件包依赖问题**，使得开发人员能够轻松地将其他开发人员开发的模块或第三方框架**集成到自己的应用程序或模块中**，**避免出现版本冲突和依赖缺失等问题**。

- 通过定义 POM 文件，**Maven 能够自动解析项目的依赖关系**，并通过 Maven **仓库自动**下载和管理依赖，从而避免了手动下载和管理依赖的繁琐工作和可能引发的版本冲突问题。

---

***一些关键点***
- 可以在 `<properies></properies>` 中设置自定义的属性
  - 如设置自定义版本属性 `<packageName.version>x.x.x</packageName.version>`，那么就可以统一管理 `<dependency></dependency>`中依赖的版本信息，即 `<verison>${packageName.version}</verison>`
- `<scope></scope>` 划定了依赖起作用的范围
  - 如打包后的 `jar/war` 等文件中是没有 `lib/junit.xx`的，因为测试的执行发生在打包之前，相关依赖只在测试过程中使用

---

***生命周期***

- 前面可以看到，在执行一个 maven命令的时候，真正执行的插件还包括前期的一些操作，如上面 `mvn install`，观察插件执行过程，实际上是在 `mvn package` 命令执行的基础上再执行 `install` 的插件。同理，打包命令也是如此。
- 即 **构建生命周期可以理解成是一组固定构建命令的有序集合，触发周期后的命令，会自动触发周期前的命令**

---

***插件、命令、周期三者关系 ***

- 周期 → 包含若干命令 → 包含若干插件
- 使用周期命令构建，简化构建过程！
- 最终进行构建的是插件

### Maven工程Build 构建配置

***项目构建是指将源代码、依赖库和资源文件等转换成可执行或可部署的应用程序的过程，在这个过程中包括编译源代码、链接依赖库、打包和部署等多个步骤。***

默认情况下，构建不需要额外配置，都有对应的缺省配置。当然了，我们也可以在pom.xml定制一些配置，来修改默认构建的行为和产物！

***例如：***

1.  指定构建打包文件的名称，非默认名称
2.  指定构建打包时，指定包含文件格式和排除文件
3.  打包插件版本过低，配置更高版本插件

构建配置是在pom.xml / build标签中指定！

***指定打包文件***

<div style="text-align:center">
    <img src="/tools4_maven/pics/未按Maven规则放置文件.png" alt="图片描述" style="margin-bottom: 1px;">
    <p>未按Maven规则放置文件</p>
</div>

如图，未按照 Maven规则将 test.xml 文件放在 resources目录下，打包生成的 war 包中对应 classes下没有 test.xml文件

**配置依赖插件**

***dependencies标签下引入开发需要的jar包！我们可以在build/plugins/plugin标签引入插件！***

***常用的插件：修改jdk版本、tomcat插件、mybatis分页插件、mybatis逆向工程插件等等！***

```xml
<build>
  <plugins>
      <!-- java编译插件，配jdk的编译版本 -->
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
          <encoding>UTF-8</encoding>
        </configuration>
      </plugin>
      <!-- tomcat插件 -->
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
         <version>2.2</version>
          <configuration>
          <port>8090</port>
          <path>/</path>
          <uriEncoding>UTF-8</uriEncoding>
          <server>tomcat7</server>
        </configuration>
      </plugin>
    </plugins>
</build>
```

### 继承和聚合


**承 vs 聚合：关键区别**
| **特性**  | **继承（Inheritance）** | **聚合（Aggregation）** |
|----------|---------------------|--------------------|
| **作用**  | 代码复用、继承父 POM 配置 | 统一管理多个子模块的构建 |
| **实现方式** | 通过 `<parent>` 关键字 | 通过 `<modules>` 关键字 |
| **父 POM 需要 `packaging=pom`？** | 是 | 是 |
| **子 POM 是否必须是父 POM 的子目录？** | 否 | 是 |
| **子 POM 是否自动继承父 POM 配置？** | 是 | 否 |
| **`mvn install` 是否会递归构建所有子模块？** | 否 | 是 |

---

- **继承** 用于 **代码复用**，允许子 POM 继承父 POM 的依赖、插件、属性等。
- **聚合** 用于 **构建管理**，一个 `mvn install` 统一编译多个模块。
- **实际开发中常常结合使用**，父 POM 既做**继承**（提供公共配置），又做**聚合**（管理模块构建）。

### Maven私服





