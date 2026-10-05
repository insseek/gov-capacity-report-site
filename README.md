# gov-capacity-report-site

《治理能力国际对比报告》的**发布仓库**。

## 这是什么

本仓库只存放**已生成**的报告文件，由
[gov-capacity-report](https://github.com/insseek/gov-capacity-report) 的流水线产出后复制至此。
**请勿直接修改本仓库的文件**——下次同步会覆盖。

- `index.html` —— 报告全文（单文件、离线可用，`<title>` 与页内声明均为报告内容）
- `netlify.toml` —— 托管配置（无构建步骤，根目录即发布目录）

## 如何更新

1. 在 [gov-capacity-report](https://github.com/insseek/gov-capacity-report) 的本地副本中构建：

   ```bash
   make report
   ```

2. 把生成物 `output/治理能力对比报告.html` 复制到本仓库根目录，
   **改名为 `index.html`**（覆盖旧文件）

3. 提交并推送：

   ```bash
   git add index.html
   git commit -m "同步 vX.Y.Z"
   git push
   ```

Netlify 检测到推送后会自动重新部署。

发布前建议核对两件事：

1. **版本号**是否与主仓库一致（`gov-capacity-report/src/catalog.py` 的 `VERSION`）
2. 报告**体积**是否仍在 1.4 MB 左右——若明显变大，可能是数据或脚本被意外内联

## 许可

**内容采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)**
（署名—非商业性使用—相同方式共享）。

- **署名**：保留报告内的作者署名与来源清单
- **非商业**：不得用于商业目的。**这不是取舍，而是上游数据的合规前提**——
  报告使用 WHO GHO、Yale EPI、QoG、SIPRI、Freedom House、Polity5 等来源的数据，
  其条款明确禁止商业使用
- **相同方式共享**：改编作品须以相同许可发布

生成本报告的**源代码**另以 MIT 许可发布，见
[gov-capacity-report](https://github.com/insseek/gov-capacity-report)；
逐源条款见该仓库的
[DATA_LICENSES.md](https://github.com/insseek/gov-capacity-report/blob/main/DATA_LICENSES.md)。
