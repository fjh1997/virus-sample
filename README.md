# virus-sample

恶意样本与取证材料归档仓库。样本仅用于安全研究、应急响应复盘和检测规则编写。

## 安全提示

- 不要在宿主机直接解压或运行样本。
- 建议只在隔离虚拟机、沙箱或离线分析环境中处理样本。
- 对外共享前确认不包含业务敏感数据、凭据或个人信息。

## 目录结构

```
samples/
  windows/
    dll-hijack-7MI0Ton0/
  tomcat/
    fkorean-20260606/
evidence/
  windows-bsod/
```

## 样本索引

| 名称 | 类型 | 时间 | 路径 | 说明 |
|------|------|------|------|------|
| 7MI0Ton0 | Windows DLL 劫持 | 2026-05-30 | `samples/windows/dll-hijack-7MI0Ton0/` | 伪装 CEF DLL，利用合法签名程序侧载 |
| fkorean | Tomcat WebShell / WAR | 2026-06-06 | `samples/tomcat/fkorean-20260606/` | CVE-2017-12615 Tomcat 容器中发现的可疑 WebApp |

## 取证材料

| 名称 | 路径 | 说明 |
|------|------|------|
| Windows BSOD 材料 | `evidence/windows-bsod/` | 蓝屏截图与 minidump 打包文件 |

## 维护约定

每个样本目录应包含:

- 原始样本压缩包
- `README.md`: 来源、现象、IOC、处置记录
- `sha256sums.txt`: 文件 hash 清单，若可取得
- `original_paths.txt`: 原始落点路径，若可取得
