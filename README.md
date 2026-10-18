# CDC：因果区分概念 · 中文精读与计算实验

论文：Goyal、Daumé III、Drouin、Sridhar，**Causal Differentiating Concepts: Interpreting LM Behavior via Causal Representation Learning**，NeurIPS 2025正式版，29页。

## 打开阅读

- **公开阅读：** https://hai426990-bot.github.io/causal-differentiating-concepts-2025/
- **先修补课：** https://hai426990-bot.github.io/causal-differentiating-concepts-2025/#00_basics
- **实际计算：** https://hai426990-bot.github.io/causal-differentiating-concepts-2025/#09_computations
- 本地：`中文精读_离线单文件.html`、`交互实验室_离线单文件.html`。
- 下载：`中文精读手册.pdf`、`基础概念补课.pdf`、`计算证据包.zip`。

无需登录、模型API或本地服务器即可阅读；浏览器本地保存进度，不跨设备同步。原论文：[正式PDF](https://proceedings.neurips.cc/paper_files/paper/2025/file/5faf0f518f39e4d6b2b595e3ca2fe0c4-Paper-Conference.pdf)。

## 内容

16节（先修、00–13、词典），覆盖正文1–9节、附录A–C、全部5个编号公式、定理1–2、定义1–2、推论1、8张原图与3张原表，并包含6张教学图、7张实际计算图（共25幅），82个中英教学词条与4个交互实验。

严谨区分：**原文报告、补充推导、条件化证明、教学诊断、本地实跑、未执行**。对证明的核对是非正式技术意见，不是作者正式勘误。

## 真正运行的实验

- 6个合成设置×3个固定种子×3个方法＝54次瓶颈训练；18份数据各20000条；18次VAE预训练另计。
- 2400条真实简介，冻结DistilBERT特征，3种子×3方法＝9次缩小半合成训练。
- 理论代数/数值诊断11类；基础/词典核验18项；保存原始测试预测并重算全部指标。
- 首轮结果保留；为补存检查点/逐因素评价预测，同协议重新执行，逐项比较，未改变超参数。

**不是官方代码复现。** 论文称代码位于补充材料，但本次未取得附件，不能由此推断作者从未发布。7B/8B原规模实验、真实拒答、LlamaScope SAE及附录敏感性系列未执行。作者原表/显著性不能凭发表均值重新构造。

本地结果不稳定、未复现作者报告的全部高分；失败设置与所有种子同样报告。预测良好不等于坐标解缠，有限数值测试不替代一般数学证明。

## 计算复核

解压计算证据包，按`experiments/README.md`安装Python 3.11及锁定依赖：

```powershell
python experiments/theory_checks.py
python experiments/verify_results.py --refit
python experiments/summarize.py
```

`--refit`使用保存的训练表征重新拟合63次评价器，不需要重新下载LM。若完整重训，见第13章与两个协议文件。

主要入口：

- `chapters/`：中文源文；`glossary.cjs`：词典。
- `experiments/`：独立实现、数据准备、训练、统计、绘图与核验。
- `results/synthetic_confirmed/`、`results/text_confirmed/`：完整计算证据。
- `results/summary.json`、`results/all_runs.csv`：机器可读汇总。
- `output/verification.md`：计算边界及验证结果。
- `build.cjs`：生成自含阅读器；`print-pdfs.cjs`：PDF。
- `stage-site.cjs`：公开文件白名单；`publish-pages.cjs`：仅向本项目创建记录匹配的仓库发布。

## 归属、许可、隐私

- 论文及原图版权归原作者。原图节选用于逐图评读，保留页码；本站链接正式全文，不镜像整篇未经确认许可的PDF。
- 本次解释、教学图和独立实现不代表作者立场。KaTeX/Marked许可文件随包保留。
- 数据镜像为`LabHC/bias_in_bios`的固定提交，卡片列MIT；原文附录列Apache-2.0，两种声明不混为一谈。
- 不发布原始人物简介、完整LM权重、缓存、凭据、机器个人路径或上一篇项目文件。
- 原始PDF、抽取全文只供本地核对，不在公开白名单或公开证据包中。

上一篇保持独立：https://hai426990-bot.github.io/causal-concepts-2402-09236/
