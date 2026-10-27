# toolshape

**校验智能体的工具调用参数是否符合声明的模式。**

`toolshape` —— 按工具的模式检查调用参数的类型、必填项与取值范围，标出不合规调用

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`toolshape.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install bmatlaw-toolshape
```

装完直接用命令名调用：

```bash
toolshape --help
```

也可以不用安装，直接把 `toolshape.py` 拷走用——它只依赖标准库。

## 为什么需要它

把「工具没调对」分成几类可修的错误，而不是笼统报失败

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 工具调用结构校验 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python toolshape.py --file input.txt
python toolshape.py --text "示例内容"
python toolshape.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 类型推断基于 AST，动态构造的返回值会标为无法判定。
- 不校验业务语义，只校验结构。

## 跑测试

```bash
python test_toolshape.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/bmatlaw/toolshape>

---

## 关于作者

bmatlaw 做工具调用结构校验相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://bmatlaw.github.io>
- 仓库：<https://github.com/bmatlaw/toolshape>

## 许可

MIT，见 [LICENSE](LICENSE)。
