# Python

欢迎加入 Epoch Lab！本项目为你的Task仓库。仓库已按阶段拆分为不同的任务模块（Task_0 ~ Task_8），请按要求在对应目录下完成开发并提交学习总结。

---

## 一、 目录组织与交付规范

每个 `Task_x` 目录下均包含该阶段的任务说明文件（`Task_x.md`）。请严格按照以下层级在对应任务文件夹内补充你的报告与代码：

```text
Epoch Task/
├── Task_0/
│   ├── Task_0.md           # 任务要求与说明
├── Task_1/
│   ├── Task_1.md
├── ...
├── Task_8/
│   ├── Task_8.md              
└── README.md               

```

> **说明**：
---

## 二、 提交与过滤规范

仓库根目录已配置 `.gitignore`。**严禁提交任何本地缓存、IDE 配置及构建产物**：

* **严禁上传**：
* Python 缓存与编译文件：__pycache__/、*.pyc
虚拟环境：.venv/、venv/、env/
测试和覆盖率缓存：.pytest_cache/、.coverage、htmlcov/
构建与打包产物：build/、dist/、*.egg-info/
类型检查与代码质量缓存：.mypy_cache/、.ruff_cache/
IDE 配置：.vscode/、.idea/
本地环境变量、日志与数据库：.env、*.log、*.sqlite3
* **文件体积限制**：GitHub 严禁单个文件超过 100MB（超过 50MB 告警）。请不要将大型测试数据集、视频或依赖压缩包直接提交到 Git 仓库中。

---

## 三、 提交流程指引

### 方式 1：本地 Git 命令行

1. **克隆本仓库到本地**：
```bash
git clone [https://github.com/Epoch-Academy/](https://github.com/Epoch-Academy/)<你的仓库名>.git
cd <你的仓库名>

```


2. **按阶段完成任务并提交**：
```bash
# 查看当前改动状态，确认没有引入 target/ 或 .idea/
git status

# 暂存当前阶段完成的任务（以 Task_0 为例）
git add Task_0/

# 提交并推送到 GitHub
git commit -m "feat: complete Task_0 code and report"
git push origin main

```



### 方式 2：GitHub 网页端上传

若本地 Git 环境暂未配置完善，可通过网页端直接交付：

1. 点击进入对应的任务目录（如 `Task_0/`）。
2. 点击右上角 **Add file** $\rightarrow$ **Upload files**。
3. 拖拽放入你编写的 `report.md` 以及代码文件。
4. 页面底部填写 Commit 说明，点击 **Commit changes**。

