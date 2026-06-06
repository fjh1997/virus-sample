# Tomcat Webshell 样本: fkorean

> 发现时间: 2026-06-06  
> 发现场景: 暴露的 Apache Tomcat 8.5.19 / CVE-2017-12615 测试容器中发现可疑 WebApp

## 样本文件

| 文件 | 说明 | SHA256 |
|------|------|--------|
| `fkorean_sample.tar.gz` | 删除前从容器文件系统打包的完整样本 | `f9bacba39dc23c98317d085f7b019ab0292ec77123306b0c96e78748a0cd6d99` |
| `sha256sums.txt` | 样本内各文件 SHA256 清单 | - |
| `original_paths.txt` | 容器内原始路径记录 | - |

## 原始路径

```
/usr/local/tomcat/webapps/fkorean
/usr/local/tomcat/webapps/fkorean.war
/usr/local/tomcat/work/Catalina/localhost/fkorean
```

## 包内结构

```
webapps/fkorean/
webapps/fkorean/WEB-INF/web.xml
webapps/fkorean/META-INF/MANIFEST.MF
webapps/fkorean/smd.jsp
webapps/fkorean.war
work/Catalina/localhost/fkorean/org/apache/jsp/smd_jsp.java
work/Catalina/localhost/fkorean/org/apache/jsp/smd_jsp.class
work/Catalina/localhost/fkorean/org/apache/jsp/smd_jsp$Runner.class
```

## IOC

```
WebApp: fkorean
JSP:    smd.jsp
WAR:    fkorean.war
URL:    /fkorean/
```

关键文件 SHA256 见 `sha256sums.txt`。

## 处置记录

2026-06-06 已在容器 `cve-2017-12615-tomcat-1` 中完成:

1. 删除前保存样本到 `/root/malware_samples/fkorean_20260606_133135/`
2. 将 Tomcat 用户 `tomcat` 的密码从 `tomcat` 修改为 `Tiantong1`
3. 删除 `fkorean` WebApp、WAR 包和 Tomcat work 编译缓存
4. 重启容器并验证 `/fkorean/` 返回 `404`
