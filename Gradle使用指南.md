# Gradle  
[Gradle官网](https://gradle.org/)  
### 一.Gradle安装  
  * 下载文件,解压后配置环境变量 `GRADLE_HOME` (文件解压硬盘位置)
  * 添加进Path环境变量
  * 终端输入以下命令,检查是否安装成功
  > gradle -v
  * 配置 `GRADLE_USER_HOME` 环境变量指定Gradle缓存jar包地址，不配置使用默认地址
---
### 二.Gradle使用  
  1. 创建build.gradle文件  
  apply: 使用java插件
  ```
  apply plugin: 'java'
  ```
  sourceCompatibility: 指定编译编译.java文件的jdk版本
  ```
  sourceCompatibility = 1.8
  ```
  
  targetCompatibility：确保class文件与targetCompatibility指定版本，或者更新的java虚拟机兼容
  ```
  targetCompatibility = 1.8
  ```
  repositories: 使用的仓库
  ```
  repositories {
    mavenCentral() // 使用maven中央仓库
    maven { url "http://repo.spring.io/libs-release" } // 指定maven仓库地址
  }
  ```
  
  dependencies：申明依赖
  ```
  dependencies {
    /*
        compile
            编译范围依赖在所有的 classpath 中可用，同时它们也会被打包

        runtime
            依赖在运行和测试系统的时候需要，但在编译的时候不需要。
            比如，你可能在编译的时候只需要 JDBC API JAR，而只有在运行的时候才需要 JDBC 驱动实现

        testCompile
            测试期编译需要的附加依赖

        testRuntime
            测试运行期需要
            不同的插件提供了不同的标准配置，你甚至也可以定义属于自己的配置项。
    */
    // 简写 # compile 'org.hibernate:hibernate-core:3.6.7.Final'
    compile group: 'org.hibernate', name: 'hibernate-core', version: '3.6.7.Final'
    testCompile group: 'junit', name: 'junit',version: '4.12'
}
  ```
  
  uploadArchives: 部署包
  ```
  uploadArchives {
    repositories {
        // 发布到本地
        flatDir {
            dirs 'repos'
        }
    }
  }
  ```
---
### 三.Gradle多模块  
TODO

---
### 四.Gradle命令  
TODO
