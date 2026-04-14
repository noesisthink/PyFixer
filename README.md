# 🛠️ PyFixer

**PyFixer** 是一款极简的 Python 代码自愈工具。它通过 **AST（抽象语法树）** 静态分析技术，一键解决“忘记写 import”和“环境缺失依赖”两大痛点。

## 📖 核心功能

* **`-im` (Import Completion)**：**补全导入**。扫描代码中正在使用的变量，自动在文件顶部插入缺失的 `import` 语句。
* **`-in` (Install Dependencies)**：**安装依赖**。自动识别 `import` 语句，检测并安装本地环境中缺失的第三方 Pip 包。
* **智能映射**：内置常用库映射表，支持处理导入名与包名不一致的情况（如 `PIL` $\rightarrow$ `pillow`）。

## 🚀 快速上手

### 1. 基础用法
在终端中指定目标脚本进行修复：

```bash
# 同时修复导入并安装依赖
python PyFixer.py target.py -im -in
```

### 2. 参数详情
| 参数 | 说明 |
| :--- | :--- |
| `file` | 目标 Python 脚本的路径 |
| `-im` | 开启「自动补全 Import」功能 |
| `-in` | 开启「自动安装缺失包」功能 |
| `--mirror` | 指定 Pip 镜像源（默认：清华源） |

## 💡 为什么使用 PyFixer？

1.  **专注逻辑**：你可以直接在代码里写 `plt.plot()` 或 `pd.DataFrame()`，无需频繁跳回文件开头手动补全。
2.  **一键部署**：拿到他人的脚本却跑不通？用 `-in` 模式让 PyFixer 自动帮你配齐所有环境。
3.  **安全高效**：基于语法树分析而非简单的字符串匹配，不会误改你的字符串内容或注释。

## ⚙️ 扩展配置
你可以直接在 `PyFixer.py` 的 `MAP` 字典中添加你常用的私有库或行业库：
```python
MAP = {
    'your_mod': ('import your_module as your_mod', 'your_pip_package'),
    # ...
}

**PyFixer：告别 ModuleNotFoundError，让代码开发行云流水。**
