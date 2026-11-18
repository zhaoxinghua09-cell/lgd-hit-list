# LGD Hit List · 爆款清单

**A registry of agent skills that survived a six-dimension audit — with the score, the evidence and the remediation trail attached.**
**一份「过了六维审计」的 Agent 技能登记册：分数、证据、整改过程都随条目一起公开。**

- Register / 登记入口：提交 issue，附包地址与自检输出（见 `HOW-TO-REGISTER.md`）
- Schema / 字段规范：`SCHEMA.md`
- Machine-readable / 机器可读：`registry.json`（AI 可直接拉取）

## 为什么存在 · Why this list exists

Most "awesome skills" lists are popularity rankings: a name, a star count, a paragraph of praise. They cannot tell you whether the package runs, whether its `SKILL.md` promises match its scripts, or whether it can phone home.

**LGD Hit List registers the opposite thing: verifiable property, not vibes.**

多数「精选清单」本质是热度榜：一个名字、一个星数、一段夸奖。它回答不了三个真问题——包能不能跑、`SKILL.md` 承诺的命令和脚本里实现的是不是同一批、以及它会不会偷偷外发数据。

**这份清单登记的是可核验属性，不是观感。**

## 六个维度 · The six dimensions

| # | 维度 · Dimension | 判据 · What is actually checked |
|---|---|---|
| 1 | 结构合规 Structure | `name` 与目录同名、kebab-case、必填字段齐、正文不超 120 行 |
| 2 | 声明-实现一致 Declared = implemented | `SKILL.md` 里出现的 `--flag` / 子命令，脚本里必须真实存在 |
| 3 | 可复跑证明 Re-runnable proof | 自带黄金集，`python tests/run_golden.py` 真实执行并给退出码 |
| 4 | 证据纪律 Evidence discipline | 每条结论可回溯到输入token/行号；不可溯源项被显式列出 |
| 5 | 安全边界 Safety boundary | 零网络、零凭据、不外发；脱敏规则存在于代码而非口号 |
| 6 | 交付可用 Delivery | 有 demo 输入、有预期输出、有边界与降级规则 |

## 登记状态 · Registration states

| 状态 | 含义 |
|---|---|
| `self-audited` | 作者自跑，分数与证据公开，**未经第三方** |
| `independent` | 由 `LGD-Eval` 评测号独立复跑通过（利益隔离，不自查自证） |
| `appealed` | 作者对扣分提出申诉，已按证据裁定（结论与理由公开） |

我们刻意把 `self-audited` 与 `independent` 分开标注：**不拿自证冒充第三方。**

## 当前条目 · Current entries

见 `registry.json`。四条自研包当前均为 `self-audited`，Python 3.13.18 复跑通过。

## 如何复跑任一登记项 · How to re-run any entry

```bash
git clone <repo> && cd <pkg>
python tests/run_golden.py        # 退出码 0 = 全通过
python scripts/review.py . --run  # 六维审计并实际执行（仅 lgd-skill-review 仓库提供此引擎）
```

## 谁在维护 · Maintained by

诺声(Logos)@SynomosAI · LGD 生态。清单本身是可核验的：每条登记都能被任何人按上面的命令重跑。
