# GitHub Pages Multi-Exam

这是一个适合部署到 GitHub Pages 的静态网页考试项目：

- `index.html`：主页，可选择不同试卷
- `exam.html`：统一考试页，按 URL 参数加载不同 XLSX 题库
- `exams/exams.json`：试卷清单
- `exams/*.xlsx`：每套试卷一个题库文件
- `.nojekyll`：关闭默认 Jekyll 处理

## 目录示例

```text
.
├─ index.html
├─ exam.html
├─ .nojekyll
├─ README.md
└─ exams/
   ├─ exams.json
   ├─ noip_basic.xlsx
   └─ noip_graph.xlsx
```

## 新增试卷方法

1. 复制一个新的 xlsx 到 `exams/` 目录。
2. 编辑 `exams/exams.json`，增加一条记录，例如：

```json
[
  {
    "id": "basic",
    "title": "NOIP 基础练习卷",
    "description": "适合基础语法与算法入门",
    "duration": 90,
    "file": "exams/noip_basic.xlsx"
  },
  {
    "id": "dp",
    "title": "NOIP 动态规划练习卷",
    "description": "新增的一套试卷",
    "duration": 120,
    "file": "exams/noip_dp.xlsx"
  }
]
```

## XLSX 模板格式

### 1) ExamConfig
第一列填 Key，第二列填 Value：

| Key | Value |
|---|---|
| Title | NOIP 基础练习卷 |
| DurationMinutes | 90 |
| Instructions | 请独立完成试卷，客观题自动判分。 |

### 2) SingleChoice
表头必须为：

| Enabled | ID | Title | OptionA | OptionB | OptionC | OptionD | Answer | Score |

其中：
- `Enabled`：填 `Y` 或 `N`
- `Answer`：填 `A/B/C/D`

### 3) FillBlank
表头必须为：

| Enabled | ID | Title | Answer | Score |

### 4) Programming
表头必须为：

| Enabled | ID | Title | Description | Score |

## GitHub Pages 部署

1. 上传整个项目到 GitHub 仓库根目录。
2. 进入仓库 `Settings` → `Pages`
3. Source 选择 **Deploy from a branch**
4. Branch 选择 `main`，Folder 选择 `/ (root)`
5. 保存后等待 Pages 生效

## 注意

如果你的 `.xlsx` 题库文件里包含标准答案，并且仓库是公开的，那么题库文件通常也能被下载查看。
因此此项目更适合：
- 练习
- 自测
- 教学演示

不适合高保密、强防作弊的正式考试。
