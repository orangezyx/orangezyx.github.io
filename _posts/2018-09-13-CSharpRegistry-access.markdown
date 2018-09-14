---
layout: post
title:  "C#在64位系统下的注册表读写"
date:   2018-09-13 21:44:12 +0800
categories: Csharp
---

今天开始了一个项目，是一个Minecraft启动器项目，使用C#语言开发

有一个功能是获取本地Jre的路径，在编写这部分代码的时候，如下

```C-like

RegistryKey javaKey = Registry.LocalMachine.OpenSubKey(@"SOFTWARE\JavaSoft\Java Runtime Environment");

string javaVersion = javaKey.GetValue("CurrentVersion").ToString();

RegistryKey javaPathKey = Registry.LocalMachine.OpenSubKey(@"SOFTWARE\JavaSoft\Java Runtime Environment\"

+ javaVersion);

string javaPath = javaPathKey.GetValue("JavaHome").ToString();

```
编译调试过程中发现变量 javaKey 的值为NULL，检查过后发现注册表路径没有错误，尝试给程序管理员权限也无果，查询相关资料得知，C#在32位系统与64位系统的注册表读写操作路径不同，上述代码只适用于32位系统，故应在读写时判断系统的位数，新建一个类
```C-like
public class RegistryHelpers
        {
            public static RegistryKey GetRegistryKey()
            {
                return GetRegistryKey(null);
            }

            public static RegistryKey GetRegistryKey(string keyPath)
            {
                RegistryKey localMachineRegistry
                    = RegistryKey.OpenBaseKey(RegistryHive.LocalMachine,
                                              Environment.Is64BitOperatingSystem
                                                  ? RegistryView.Registry64
                                                  : RegistryView.Registry32);

                return string.IsNullOrEmpty(keyPath)
                    ? localMachineRegistry
                    : localMachineRegistry.OpenSubKey(keyPath);
            }
        }
```
将原来的读写代码改成如下
```C-like
RegistryKey javaKey = RegistryHelpers.GetRegistryKey(@"SOFTWARE\JavaSoft\Java Runtime Environment");
string javaVersion = javaKey.GetValue("CurrentVersion").ToString();
RegistryKey javaPathKey = RegistryHelpers.GetRegistryKey(@"SOFTWARE\JavaSoft\Java Runtime Environment\"
+ javaVersion);
string javaPath = javaPathKey.GetValue("JavaHome").ToString();
```
问题就解决了
![running_success.png](https://upload-images.jianshu.io/upload_images/6539448-e3f9e39fd92f829f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)