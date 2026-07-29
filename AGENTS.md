## Git 提交信息

- 本仓库中由 Codex 创建的所有 Git 提交，提交信息必须固定为 `Update`。
- 除非用户明确指定其他提交信息，否则不得自行概括、描述或扩展提交内容。

## org pub（整理论文条目：Conference / Journal / Arxiv）

当用户说 **“org pub”** 时，你需要把用户给出的论文信息（截图 / 文字 / URL）整理成本站可用的 Markdown，并完成插入。

### 目标文件（以当前仓库为准）

- 论文条目文件（按类别选择其一）：
  - Conference：`_includes/pubs/Conferences/<FILENAME>.md`
  - Journal：`_includes/pubs/Journals/<FILENAME>.md`
  - Preprint：`_includes/pubs/Arxiv/<FILENAME>.md`
- 汇总页文件：`_pages/includes/pub_short.md`（注意：这是一个 `.md` 文件，位于 `_pages/includes/` 目录中）
- 插入位置：`_pages/includes/pub_short.md` 对应小节下：
  - Preprint → `**Preprints**`
  - Conference → `**Conferences**`
  - Journal → `**Journals**`

### 输入（用户可能提供的形式）

- 截图：录用通知 / OpenReview / arXiv / CVF / 会议官网 / 论文主页等
- 文字：标题、作者、会议、链接、口头/海报、代码等
- URL：论文页 / arXiv / OpenReview / 会议 virtual site / GitHub 等

### 你必须收集/确认的信息（缺了就问）

- `category`：Conference / Journal / Preprint（用户不指定则你根据 venue/链接判断；不确定就问）
- `venue`：会议简称（如 CVPR / NeurIPS / ICLR / AAAI / IJCAI / ICCV / ECCV …）
- `year`：会议年份（如 2025）
- `title`：论文标题（保持官方大小写）
- `authors`：作者顺序（与最终版本一致）；把 **Ziheng Chen** 加粗；通讯作者用 `<sup>†</sup>`（例如 `**Ziheng Chen<sup>†</sup>**`）；共同一作用 `<sup>*</sup>`（例如 `Name<sup>*</sup>`）
- `paper_url`：标题要链接到的页面（优先 arXiv / OpenReview / 官方 PDF）
- `highlights`（可选）：如 Oral / Spotlight / Best Paper 等（有就加）
- `resources`（可选）：Code / Project / PDF / Slides / Poster / Video / Dataset 等链接（有就加，没有就不写）

### 文件命名规则（严格对齐仓库既有风格）

文件名格式为：`[year]-[venue]-[short_name].md`

1) 先在目标子文件夹里找**同一 venue / 同一年**的既有文件名风格并复用：
   - Conferences：`_includes/pubs/Conferences/`
   - Journals：`_includes/pubs/Journals/`
   - Arxiv：`_includes/pubs/Arxiv/`
2) 文件名格式固定为：
   - `YYYY-<VENUE>-<SHORT_NAME>.md`
   - 例：`2025-NeurIPS25-GyroAtt.md` / `2024-CVPR-SPDMLR.md` / `2024-TIP-ALEM.md` / `2024-Arxiv-Cho_Metric.md`
   - 其中 `[venue]` 以该子文件夹的既有文件为准（可能带年份后缀，例如 `NeurIPS25` / `CVPR25`，也可能不带，例如 `TIP` / `Arxiv`）
3) `[short_name]` 规则：
   - 用论文常用缩写/方法名/项目名（如 `SPDMLR`, `GyroBN`），只用字母数字和短横线；避免空格；保证唯一。

### 条目 Markdown 格式（通用；badge 按类别选择）

把每篇论文写成一个条目文件，内容结构如下（换行/标点保持一致）：

- 第一行（badge）：
  - Conference：`- <span class="conf-badge">VENUE YEAR</span>`
  - Journal：`- <span class="journal-badge">VENUE YEAR</span>`
  - Preprint：`- <span class="arxiv-badge">Arxiv YEAR</span>`
- 第二行：`[Title](paper_url),`
- 第三行：作者列表（逗号分隔，句末句号）；其中 `**Ziheng Chen**`（如通讯作者则 `**Ziheng Chen<sup>†</sup>**`；`<sup>†</sup>` 表示通讯作者；`<sup>*</sup>` 表示共同一作）
- 亮点行（可选）：例如
  - Oral（红色）：`<span style="color:#d32f2f"><strong>(Oral)</strong></span>`
  - Spotlight / Highlight（绿色）：`<span style="color:#2e7d32"><strong>(Spotlight)</strong></span>` 或 `<span style="color:#2e7d32"><strong>(Highlight)</strong></span>`
- 资源行（可选，逐行追加）：例如
  - `[[Code](...)]`
  - `[[Slides](...)]`
  - `[[Poster](...)]`
  - `[[Video](...)]`

注意：如果用户给了现成链接但不确定类型（Slides/Poster/Video），优先按链接指向内容判断；判断不了就问。

### 典型示例（Conferences）

- `- <span class="conf-badge">ICLR 2024</span>`
- `[A Lie Group Approach to Riemannian Batch Normalization](https://openreview.net/pdf?id=okYdj8Ysru),`
- `**Ziheng Chen**, Yue Song, Yunmei Liu, Nicu Sebe.`
- `[[Code](https://github.com/GitZH-Chen/LieBN)]`
- `[[Slides](https://github.com/GitZH-Chen/LieBN/raw/main/ICLR24_LieBN_PPT.pdf)]`
- `[[Poster](https://github.com/GitZH-Chen/LieBN/raw/main/ICLR24_LieBN_Poster.pdf)]`
- `[[Video](https://iclr.cc/virtual/2024/poster/17806)]`

### 插入到 `pub_short.md`

1) 在对应小节下新增一行 include（按类别选择其一）：
   - Preprint：`{% include pubs/Arxiv/<FILENAME>.md %}`
   - Conference：`{% include pubs/Conferences/<FILENAME>.md %}`
   - Journal：`{% include pubs/Journals/<FILENAME>.md %}`
2) 排序规则：按年份从新到旧（与现有列表一致）；同一年内把新条目放在该年同 venue 的最上方。
3) 若已存在同名 include 或同一论文条目，改为更新原文件/原 include，避免重复。

### 输出要求（你要直接改代码库）

- 新增/更新：`_includes/pubs/<CATEGORY_DIR>/<FILENAME>.md`
- 修改：`_pages/includes/pub_short.md`（只改对应小节相关行）
- 最后用一句话告诉用户：新增了哪个文件、并插入到了哪里。
