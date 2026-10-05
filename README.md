# gov-capacity-report-site

《治理能力国际对比报告》的**发布仓库**。

## 这是什么

本仓库只存放**已生成**的报告文件，由 [`gov-capacity-report`](../gov-capacity-report)
的流水线产出后复制至此。**请勿直接修改本仓库的文件**——下次同步会覆盖。

- `index.html` —— 报告全文（单文件、离线可用，`<title>` 与页内声明均为报告内容）
- `netlify.toml` —— 托管配置（无构建步骤，根目录即发布目录）

## 如何更新

在 `gov-capacity-report` 仓库中：

```bash
make report                                  # 重新生成交付物
cp output/治理能力对比报告.html \
   ../gov-capacity-report-site/index.html    # 同步到本仓库
cd ../gov-capacity-report-site
git commit -am "同步 vX.Y.Z" && git push
```

Netlify 检测到推送后会自动重新部署。

## 许可

**内容采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)**
（署名—非商业性使用—相同方式共享）。

- **署名**：保留报告内的作者署名与来源清单
- **非商业**：不得用于商业目的。**这不是取舍，而是上游数据的合规前提**——
  报告使用 WHO GHO、Yale EPI、QoG、SIPRI、Freedom House、Polity5 等来源的数据，
  其条款明确禁止商业使用
- **相同方式共享**：改编作品须以相同许可发布

生成本报告的**源代码**另以 MIT 许可发布（在 `gov-capacity-report` 仓库），
与内容许可相互独立。逐源条款见该仓库的 `DATA_LICENSES.md`。
