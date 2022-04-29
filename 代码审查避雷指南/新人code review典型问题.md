# 如何避免被code review毒打，总结cr中的典型问题
<br><br><br>

# 1 命名不规范
<br>

## 典型问题：
### 1.取名过于简单，无法清晰表达含义
```
//单字符,简短单词作为变量名
bool flag = false;
for(f in markedFiles){
    //handle each marked file
}
```
### 2.命名风格不一，影响代码阅读
```
//多种风格的方法名
IsProcessRunning()
CheckIfPageClosed()
```
### 3.没参照规范命名
<br>

## 建议：
### 1.遵循已有的命名规范：
### -若公司/团队对于命名有规范文档，应好好研究。
### -可以适当参照现有代码的命名风格。
### 2.命名要能够清晰展现有关的含义(好的命名的基本要求)
### -较长而清晰的命名优于简短而模糊的命名，不要过于追求简短。
### -为一个好的命名花费的思考是值得的。
### 3.命名技巧学习：
### -多阅读书籍、教程、知名源码等等，学习命名思路和技巧。

<br>

# 2 注释不合规
<br>

## 典型问题：
### 1.修改代码不更新注释,造成误导
```
//do something about A 
Function()
{
    // do some actions about B
}
```
### 2.无意义的注释(如日志型日志,废弃的代码)
```
/*
 * Date: 1 Jan
 * Author: Hongtao
 * Change: Update this function for fixing bug : ...
 * ........
*/
Function(){
    /*
    OldFlow();
    */
    NewFlow();
}
```
### 3.过多篇幅的注释
```
/*
    multi-lines
*/
Function(){
    ......
}
```
<br>

## 建议：
### 1.遵循已有的注释规范：
### -若公司/团队对于命名有规范文档，应好好研究。
### -可以适当参照现有代码的注释风格。
### 2.避免写出坏注释：
### -不达意的注释
### -含有误导的注释
### -与逻辑无关的注释
### 3.及时更新注释
### 4.清晰的代码是不需要太多注释说明的
<br>

# 3 函数封装和复用
<br>

## 典型问题：
### 1.不使用公司/团队封装的工具库，自己重新实现
```
//文件IO工具类的封装
class FileUtility{
    Read(){}
    Write(){}
    Copy(){}
    Delete(){}
    ...
}
//字符串格式处理工具类的封装
class StringUtility(){
    EncodeString()
    DecodeString()
    Foramt()
    ToUpper()
    ToLower()
    ...
}
```
### 2.函数过长，缺乏提炼
```
Function()
{
    // do A
    ...
    // do B
    ...
    // do C
    ...
    ...
}
```
### 3.重复代码不做复用
<br>
## 建议：
### 1.底层逻辑编码时，先看看是否被公司/团队进行过封装。
### -字符串等数据结构的处理
### -文件、日期等类型的处理
### -异步操作，事件绑定等处理
### 2.按照职责设计和提炼函数,尽量做到函数单一职责
### 3.相同逻辑的代码积极复用
<br>
# 4 不合理的变量定义
<br>

## 典型问题：
### 1.变量定义不考虑解耦
```
//方法体中的整型/字符串定义
class WebpageLauncher(){
    public int LaunchLoginPage(){
        string loginUrl = "www.xxx.com/login"
        ......
        if(error){
            return 1001;
        }
    }
    public LaunchHelpPage(){
        string helpUrl = "www.xxx.com/help"
        ......
        if(error){
            return 1002;
        }
    }
}
```
### 2.使用常量代替应该动态生成的内容
```
const string systemPath = "C:\\";
```
<br>

## 建议：
### 1.使用字面量定义时，考虑能否解耦
### -类中使用的常量，可以定义为类中的静态常量
### -全局使用的常量，通常被集中定义在某些文件中(config、table、global)。
### 2.能够在运行时获取的内容(系统API、网络、文件)，不应被定义在代码中。
<br><br><br><br>


