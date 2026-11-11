# HW1 - Setup

> **官方标题**：Homework 1: Setup（Due Fri Aug 29）
> **来源**：[HW01 官方页面](../../../../SOURCE/cs61b-fa25-site/fa25.datastructur.es/homeworks/hw01/index.html)
> **性质**：官方作业。骨架文件取自 `Berkeley-CS61B/skeleton-fa25/hw01`，与官方一致。

---

## 总起

- **一句话定位**：把工具链装好，并用一个故意写错的 `Arithmetic.java` 走通「运行 → 跑测试 → 修 bug → 提交」的完整作业流程。
- **覆盖知识点**：终端、Git/GitHub SSH、仓库结构、IntelliJ 导入、JDK 21、JUnit 5 + Truth 测试。
- **题目地图**：Task 1–9 中只有 **Task 8（修代码）** 和 **Task 9（提交）** 需要动手写东西，Task 1–7 是环境配置，步骤见 [Lab00](../../Lab/Lab00/README.md)。
- **对应资源**：[Assignment Workflow](../../../../SOURCE/cs61b-fa25-site/fa25.datastructur.es/resources/assignment-workflow/index.html)（每个作业在 IntelliJ 里的打开方式都要按这篇来）

---

## 文件说明

| 文件 | 用途 | 说明 |
|---|---|---|
| `src/Arithmetic.java` | 作业代码 | 官方骨架原样保留：`product` 正确，`sum` 故意写错 |
| `tests/ArithmeticTest.java` | 官方测试 | JUnit 5 + Google Truth，**不要改** |

---

## 题目（官方 Task 8 原文 + 中文要点）

1. 打开 IntelliJ，按 Assignment Workflow 中 “Opening in IntelliJ” 的步骤导入项目。
2. 侧边栏应能看到 `Arithmetic` 和 `ArithmeticTest`。
3. 运行 `Arithmetic` 的 `main`。
4. 控制台会让你输入两个整数，**先别急着修** —— 官方要求先观察到结果是错的。
5. 运行 `ArithmeticTest`：`Test product correctness` 通过，`Test sum correctness` 失败。
6. 修改 `Arithmetic.java` 让测试全部通过，然后重新运行测试确认。

> 提示：`sum` 的方法注释里已经写明它 “incorrectly”，改的是实现，不是测试。

---

## 运行方式

**IntelliJ**：`File → Project Structure → Libraries → +` 添加 `library-fa25` 整个目录，否则 `import edu.princeton.cs.algs4.StdIn` 会报 `package does not exist`。

**命令行**（PowerShell，在 `Hw/HW1` 下）：

```powershell
# 编译（依赖 algs4.jar）
javac -cp "..\..\..\..\SOURCE\hw_proj\library-fa25\*" -d out src\Arithmetic.java

# 运行
java -cp "out;..\..\..\..\SOURCE\hw_proj\library-fa25\*" Arithmetic

# 跑测试（需要 junit-platform-console-standalone.jar 和 truth 相关 jar）
java -jar "..\..\..\..\SOURCE\hw_proj\library-fa25\junit-platform-console-standalone-*.jar" `
     -cp "out;tests;..\..\..\..\SOURCE\hw_proj\library-fa25\*" --scan-classpath
```

> 注意：本机 `SOURCE/hw_proj/library-fa25` 目前是空目录（尚未 clone），上面命令会因找不到 jar 失败。先 `git clone git@github.com:Berkeley-CS61B/library-fa25.git`，或直接用 IntelliJ 跑测试。

---

## 提交（Task 9 官方命令）

```bash
git status
git add hw01/src/Arithmetic.java
git commit -m "fixed Arithmetic.java in hw01"
git push origin main
```

然后到 Gradescope 选择 GitHub 仓库 `fa25-s<学号>` 的 `main` 分支提交，确认拿满分。

**注意目录名**：官方仓库里是 `hw01`（全小写）。本地用 `HW1` 不影响练习，但如果要直接对接官方仓库，`git add` 的路径得写成 `hw01/src/Arithmetic.java`。

---

## 验收标准

- [ ] `Arithmetic` 运行后，两数之和与两数之积都正确
- [ ] `ArithmeticTest` 两条测试全绿
- [ ] `git status` 显示工作区干净，GitHub 上能看到改动
- [ ] Gradescope 显示满分

---

## 易错点

- **先修再跑**：跳过第 4、5 步直接改代码，会错过「看懂测试失败信息」这一步。
- **改测试**：`tests/` 是只读的，改它没有意义，评分看的是 `src/`。
- **忘加 library**：IntelliJ 里没加 `library-fa25`，`StdIn` 直接标红。
- **提交了编译产物**：`out/`、`*.class` 已在根目录 `.gitignore` 里，别用 `git add .` 强行加进来。
