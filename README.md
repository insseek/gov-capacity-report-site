# gov-capacity-report-site

《国家治理能力的国际比较》的**发布仓库**。

## 🌐 线上地址

| 托管 | 地址 | 说明 |
|---|---|---|
| **GitHub Pages** | https://insseek.github.io/gov-capacity-report-site/ | 与本仓库文件**逐字节相同**，适合核对 |
| **Netlify** | https://gov-capacity-report.netlify.app/ | 访问更快，但服务端会注入内容（见下） |

两个地址指向**同一份文件**，互为备份。推送到 `main` 后两边都会自动重新部署。

### 为什么两个地址不完全一样

Netlify 在**服务端**对每个响应做两处注入（不修改仓库里的文件）：

1. 顶部一段介绍 Netlify 的 HTML 注释（约 324 字节）
2. 末尾 `<script async src="/.netlify/scripts/hud?...">`（约 186 字节）

**页面内容本身逐行相同**，差异只有这两处。因此：

- 要验证「发布的就是构建产物」→ 用 **GitHub Pages**
- 只想让读者打开 → 两个都行，Netlify 通常更快

`index.html` 的「离线可用」说的是**文件本身**：它内联了 ECharts 与全部数据，
**不含任何外部资源引用、不含带 `src` 的 script**。下载下来断网也能打开。

## 这是什么

本仓库只存放**已生成**的报告文件，由
[gov-capacity-report](https://github.com/insseek/gov-capacity-report) 的流水线产出后复制至此。
**请勿直接修改本仓库的文件**——下次同步会覆盖。

| 文件 | 说明 |
|---|---|
| `index.html` | 报告全文（单文件、离线可用；`<title>` 与页内声明均为报告内容） |
| `netlify.toml` | Netlify 托管配置（无构建步骤，根目录即发布目录） |
| `LICENSE` | 内容许可说明（CC BY-NC-SA 4.0） |

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

推送后 Netlify 与 GitHub Pages 都会自动重新部署。

发布前建议核对两件事：

1. **版本号**是否与主仓库一致（`gov-capacity-report/src/catalog.py` 的 `VERSION`）
2. 报告**体积**是否仍在 1.4 MB 左右——若明显变大，可能是数据或脚本被意外内联

## 许可

**内容采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)**
（署名—非商业性使用—相同方式共享），详见 [LICENSE](LICENSE)。

- **署名**：保留报告内的作者署名与来源清单
- **非商业**：不得用于商业目的。**这不是取舍，而是上游数据的合规前提**——
  报告使用 WHO GHO、Yale EPI、QoG、SIPRI、Freedom House、Polity5 等来源的数据，
  其条款明确禁止商业使用
- **相同方式共享**：改编作品须以相同许可发布

生成本报告的**源代码**另以 MIT 许可发布，见
[gov-capacity-report](https://github.com/insseek/gov-capacity-report)；
逐源条款见该仓库的
[DATA_LICENSES.md](https://github.com/insseek/gov-capacity-report/blob/main/DATA_LICENSES.md)。
