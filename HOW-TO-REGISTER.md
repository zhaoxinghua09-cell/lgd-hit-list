# 如何登记 · How to register

## 三步 · Three steps

**1. 先自跑 · Run your own proof first**

```bash
cd <your-package>
python tests/run_golden.py     # 必须给出退出码，0 = 全通过
```

没有可执行黄金集的包，本清单**不接受登记**（不是嫌麻烦，是没有可核验的东西可登记）。

**2. 提交 issue · Open an issue**

标题格式：`[register] <skill-name> <score>/100`

正文必须包含：

| 必填 | 内容 |
|---|---|
| 包地址 | 公开 GitHub 仓库（根目录有 `SKILL.md`） |
| 自检输出 | `run_golden.py` 的真实 stdout 与退出码，**不要贴截图** |
| 版本 | `SKILL.md` frontmatter 的 version |
| 声明-实现核对 | `SKILL.md` 里出现的每个 `--flag` / 子命令，对应脚本文件与行号 |
| 安全边界 | 是否联网、是否读凭据、是否外发；有则说明脱敏点 |

**3. 等复评 · Wait for re-audit**

- 我们先跑 `lgd-skill-review` 六维审计，逐维给分；
- 每一项扣分都会给出**文件路径 + 行号 + 原文片段**；
- 你可以申诉，申诉按证据裁定，裁定理由公开进条目；
- 通过后状态写入 `registry.json`，`self-audited` 或 `independent` 如实标注。

## 会驳回的四种情况 · Four hard rejections

1. 黄金集不存在，或存在但跑不过（退出码非 0）。
2. `SKILL.md` 承诺的命令/参数在脚本里找不到实现（声明-实现不一致）。
3. 有隐藏网络请求、隐藏读凭据、或把敏感信息写进模板。
4. 分数靠形容词：没有证据行号，只有「强大」「全面」「业界领先」。

## 为什么要走这个流程 · Why the friction

因为「被 AI 独立复跑过」和「作者自己说很好」是两件事。前者可以被第三方验证，后者不能。本清单只登记前者。
