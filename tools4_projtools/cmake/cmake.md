## references
[菜鸟教程cmake](https://www.runoob.com/cmake/cmake-tutorial.html)
[CMake使用教程](https://blog.csdn.net/weixin_43717839/article/details/128032486?ops_request_misc=%257B%2522request%255Fid%2522%253A%25229F450FDE-30BC-4157-9BF3-A379508D7A80%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=9F450FDE-30BC-4157-9BF3-A379508D7A80&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-128032486-null-null.142^v100^control&utm_term=cmake%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187)


## simple example

- `touch main.c CMakeLists.txt` 创建源码文件 `main.c` 和 `CMakeLists` 文件
- 编写文件内容
- `cmake .` 运行，会新生成 4 个文件
  -  ***`CMakeCache.txt`***
    - 存储了 CMake 在配置过程中的缓存信息
    - 这个文件是持久的，它允许 CMake 在后续的配置过程中记住之前设置的变量值，从而加快构建过程
    - 可以通过编辑该文件来改变一些配置选项，建议使用 `cmake -D <variable>=<value> `命令来设置变量
  - ***`CMakeFiles`***
    - 一个目录，包含了 CMake 生成的构建系统文件
  - ***`cmake_install.cmake`***
    - 脚本文件，它包含了安装项目所需的指令
  - ***`MakeFile`***
    -  CMake 生成的主要 Makefile，它包含了构建项目所需的所有指令
    -  执行 `make` 命令时，这个 Makefile 会被用来编译和链接项目中的源代码，生成最终的可执行文件或库文件
 -  `make` 生成可执行文件
    - `make clean` 会删除生成的可执行文件 

## `CMakeLists.txt`
### same dir
```text
// simple

cmake_minimum_required (VERSION 2.8)

project (demo)

add_executable(main main.c testFunc.c testFunc1.c)



// more file in the same directory

aux_source_directory(. SRC_LIST)

add_executable(main ${SRC_LIST})


// specify certain source files to be compile

set(SOURCE_FILES
    ./main.c
    ./testFunc.c
    ./testFunc1.c)

add_executeable(main ${SOURCE_FILES})
```

1. `cmake_minimum_required(VERSION <version>)` 指定 `CMake` 最低版本要求
2. `project(<project_name> [<language>...])` 定义项目名称和使用的编程语言， 如 `project(my_demo) CXX`
3. `add_executable(<target> <source_files>...)` 指定生成的可执行文件，和其源文件
   1.如果同一目录下有 ***多个源文件，在 `add_executable` 中添加所有源文件即可***
4. `aux_source_directory(. SRC_LIST)` 扫描当前目录 `.`下的所有源文件（`.cpp, .c `），并将其路径存入 `SRC_LIST` 中, 后续使用  `${SRC_LIST}` 变量表明当前目录下所有源文件的路径 （`SRC_LIST` 可自定义）
5. `set(<variable> <value>...)` 设置变量的值，如上，选择指定要加入的源文件


### different dirs

```text
cmake_minimum_required(VERSION 2.8)

project(MyTestCmakeProj C)

include_directories(test_func test_func1)

aux_source_directory(test_func SRC_LIST)
aux_source_directory(test_func1 SRC_LIST1)

add_executable(main main.c ${SRC_LIST} ${SRC_LIST1})
```


1. `include_directories(<dirs>...)` 添加头文件搜索路径
2. 执行多个 `aux_source_directory(scan_dir path_list)` 分别将不同目录下的文件路径存入 变量`path_list`


## project-level structure

### 正规项目结构
- `src` 存放源文件
- `include` 存放头文件
- `build` 存放生成的对象文件中间文件等
- `bin` 存放最终生成的可执行文件


<div style="text-align:center">
    <img src="/tools4_projtools/pic_src/项目级结构.png" alt="项目级结构" style="margin-bottom: 1px;">
    <p>项目级结构</p>
</div>

- `cmake` 
  - `cmake dir<. ..>` 会到 `dir` 目录中寻找 `CMakeLists.txt` 来执行，如 `cmake ..` 就是到当前所在目录的父目录中去寻找  
  - 执行产生的中间文件对象文件等，会生成在所执行的目录下
  - 所以在 `build` 目录下执行 `cmake ..` 会搜索到 `.` （父目录）中的 `CMakeLists.txt` 文件，然后将产生的附带文件生成在 `build` 目录下，从而 不会跟源码文件混在一起

### 项目目录下的`CMakeLists.txt`
```text
cmake_minimum_required(VERSION 2.8)

project(MyTestCmakeProj C)

add_subdirectory(src)
```
`add_subdirectory(source_dir [binary_dir] [EXCLUDE_FROM_ALL])
` 命令非常有用
1. ***`add_subdirectory ` 用于将一个子目录添加到 构建中，允许将一个项目分割成多个子项目，每个项目都有自己的 `CMakeLists.txt` 文件***
2. ***`source_dir`*** 
   1. 子项目源码目录的路径（包含源码和子项目自己的`CMakeLists.txt`）
   2. 该目录若为相对路径，则为相对于该 `CMakeLists.txt` 文件的路径
   3. 如果子目录中包含其子项目自己的 `CMakeLists.txt`，会继续处理内层子项目的 `CMakeLists.txt`
3. ***`binary_dir`***
   1. 指定子目录构建目标的生成位置目录
   2. 若为相对路径，则相对于 `cmake` 命令执行的目录
   3. 如 `add_subdirectory(lib)` 表CMake 在构建过程中包含 lib 目录，并且 lib 目录中的 CMakeLists.txt 将被用来配置和生成该目录的构建目标
   4. 如 `add_subdirectory(lib lib_build)` 会将 lib 目录的构建目标放在 lib_build 目录中
4. ***`EXCLUDE_FROM_ALL`***
   1.  如 `add_subdirectory(lib EXCLUDE_FROM_ALL)` 会排除 `lib` 目录中的构建目标，使其不包含在默认的 all 目标中
   2. ***CMake 构建系统中运行 make 命令时会构建所有在 CMakeLists.txt 文件中定义的构建目标。这些目标被包含在特殊的 all 目标中***

### src`子目录下的`CMakeLists.txt`

```text
aux_source_directory(. SRC_LIST)

include_directories(../include)

add_executable(main ${SRC_LIST})

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
```

- `aux_source_directory(. SRC_LIST)` 中的 `.` 表扫描当前目录 `src` 下的所有源码文件，搜集路径存入 `SRC_LIST`
- `include_directories(../include)` 将 项目目录下`include`目录中的 `.h` 文件都加入头文件搜索路径
- `set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)` 其中 有两个系统自带的预定义变量
  - `EXECUTABLE_OUTPUT_PATH` 生成的目标可执行文件的存放位置
  - `PROJECT_SOURCE_DIR` 项目的根目录
  - 即 把 `main` 生成到 `bin` 目录下

### 只用最外层 `CMakeLists.txt`
```text
cmake_minimum_requiored(VERSION 2.8)

project(MyTestCmakeProj C)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

aux_source_directory(src SRC_LIST)

include_directories(include)

add_executable(main ${SRC_LIST})
```




