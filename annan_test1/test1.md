
# 课程：体系结构与设计模式  
## 实验名称：安装课程所需相关开发环境和软件  

### 基本信息  
- **专业**：软件工程  
- **班级**：软工一班  
- **学号**：121052022037  
- **姓名**：陈安楠  
- **实验日期**：2025年4月19日  


## 实验内容与过程  

### 一、下载与配置 Android Studio  
#### 1. SDK 安装失败问题  
- **问题描述**：首次安装 Android Studio 时，SDK 组件下载过程中频繁出现超时或中断，导致安装失败。  
- **解决方法**：  
  通过设置 HTTP 代理为腾讯镜像源加速下载，具体配置如下：  
  - 打开 Android Studio 的 **Settings > Appearance & Behavior > System Settings > HTTP Proxy**  
  - 选择 **Manual proxy configuration**，设置代理地址为：  
    ```  
    HTTP Proxy: mirrors.cloud.tencent.com  
    Port: 80  
    ```  
  - 勾选 **No proxy for** 并填入 `localhost, 127.0.0.1`，应用配置后重新启动 SDK 安装。  

#### 2. Gradle 配置失败问题  
- **问题描述**：项目同步时 Gradle 依赖下载缓慢，使用 VPN 工具仍无法解决。  
- **解决方法**：  
  在项目级 `build.gradle` 中配置多镜像源加速，具体代码如下：  
  ```gradle  
  buildscript {  
      repositories {  
          // 腾讯云 Gradle 镜像  
          maven { url "https://mirrors.cloud.tencent.com/gradle/" }  
          google()  
          mavenCentral()  
      }  
      dependencies {  
          classpath "com.android.tools.build:gradle:8.4.0"  
      }  
  }  
  
  allprojects {  
      repositories {  
          // 阿里云镜像（覆盖 Maven Central、Google、JCenter 等）  
          maven { setUrl("https://maven.aliyun.com/repository/public/") }  
          maven { setUrl("https://maven.aliyun.com/repository/google/") }  
          maven { setUrl("https://maven.aliyun.com/repository/jcenter/") }  
          maven { setUrl("https://maven.aliyun.com/repository/gradle-plugin/") }  
          // 华为云镜像  
          maven { setUrl("https://repo.huaweicloud.com/repository/maven/") }  
          // 腾讯云镜像  
          maven { setUrl("https://mirrors.cloud.tencent.com/nexus/repository/maven-public/") }  
          // 网易镜像  
          maven { setUrl("https://mirrors.163.com/maven/repository/maven-public/") }  
          google()  
          mavenCentral()  
      }  
  }  
  ```  
  配置完成后，重新同步项目，Gradle 依赖成功下载，环境运行正常。  

### 二、学习 Markdown 语法  
本次实验同步学习了基础 Markdown 语法，包括：  
- **标题**：通过 `#` 到 `######` 定义不同层级标题（如 `# 一级标题`）。  
- **列表**：有序列表（`1. 项目一`）和无序列表（`- 项目一`）。  
- **代码块**：使用反引号 `` ` `` 包裹单行代码，或通过 ```java 标识代码块并指定语言。  
- **格式修饰**：`**加粗**`、`*斜体*`、`~~删除线~~` 等文本样式。  


## 实验总结  
通过配置镜像源解决开发环境安装问题，掌握 Markdown 基础语法，提升问题排查能力。