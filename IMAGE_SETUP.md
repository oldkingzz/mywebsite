# 图片设置指南

## ✅ 已修复的问题

我已经修复了以下问题：

1. **修复了 Robocon 项目的图片路径错误**
   - 原路径：`static/images/projects/mywebsite/static/images/projects/robocon.png`（错误）
   - 新路径：`/images/projects/robocon.png`（正确）✅

2. **修复了重复的 `content` 键错误**
   - Projects 部分的两个项目都有重复的 content 定义
   - 已合并为单个 content 字段 ✅

3. **临时禁用了缺少的图片**
   - Achievements 部分的 3 张图片已注释掉
   - IEEE Publication 项目的图片已注释掉
   - 网站现在可以正常显示，不会因为缺少图片而报错 ✅

---

## 📁 当前图片状态

### ✅ 已有的图片：
- `static/images/me.jpg` - 你的头像 ✅
- `static/images/hero.svg` - 首页背景图 ✅
- `static/images/projects/robocon.png` - Robocon 项目图片 ✅

### ❌ 缺少的图片（已临时禁用）：
- `static/images/achievements/ieee-paper.jpg` - IEEE 论文图片
- `static/images/achievements/robocon.jpg` - Robocon 团队照片
- `static/images/achievements/competition.jpg` - 比赛获奖照片
- `static/images/projects/fault-detection.jpg` - 故障检测项目图片

---

## 🎯 如何添加缺少的图片

### 步骤 1：准备图片文件

为每个缺少的图片准备一张图片：

**Achievements 图片建议：**
- `ieee-paper.jpg` - 可以是论文的截图、会议照片、或相关研究图表
- `robocon.jpg` - Robocon 团队合照或机器人照片
- `competition.jpg` - 比赛现场照片或获奖证书

**Projects 图片建议：**
- `fault-detection.jpg` - 可以是研究流程图、模型架构图、或实验结果图表

**图片规格建议：**
- 格式：JPG 或 PNG
- 尺寸：800x600 像素或更大
- 文件大小：< 500KB（优化后）

### 步骤 2：将图片放到正确的目录

```bash
# 进入项目目录
cd mywebsite

# 复制 Achievements 图片
cp /path/to/ieee-paper.jpg static/images/achievements/
cp /path/to/robocon-team.jpg static/images/achievements/robocon.jpg
cp /path/to/competition.jpg static/images/achievements/

# 复制 Projects 图片
cp /path/to/fault-detection.jpg static/images/projects/
```

### 步骤 3：在 hugo.yaml 中取消注释

打开 `hugo.yaml`，找到以下行并取消注释（删除开头的 `#`）：

**Achievements 部分（约第 279-285 行）：**
```yaml
# 修改前：
# image: /images/achievements/ieee-paper.jpg  # 添加图片后取消注释

# 修改后：
image: /images/achievements/ieee-paper.jpg
```

对以下三行做同样的操作：
- 第 279 行：`# image: /images/achievements/ieee-paper.jpg`
- 第 282 行：`# image: /images/achievements/robocon.jpg`
- 第 285 行：`# image: /images/achievements/competition.jpg`

**Projects 部分（约第 319 行）：**
```yaml
# 修改前：
# image: /images/projects/fault-detection.jpg  # 添加图片后取消注释

# 修改后：
image: /images/projects/fault-detection.jpg
```

### 步骤 4：本地预览

```bash
cd mywebsite
hugo server -D
```

在浏览器打开 `http://localhost:1313/mywebsite/` 检查图片是否正确显示。

### 步骤 5：提交并部署

```bash
git add static/images/
git add hugo.yaml
git commit -m "Add achievement and project images"
git push origin main
```

---

## 🎨 临时解决方案：使用占位图

如果你暂时没有合适的图片，可以使用以下方法：

### 方案 1：使用免费图片网站

从以下网站下载相关主题的免费图片：
- **Unsplash**: https://unsplash.com/
- **Pexels**: https://www.pexels.com/
- **Pixabay**: https://pixabay.com/

搜索关键词：
- "robotics" - 机器人相关
- "artificial intelligence" - AI 相关
- "engineering" - 工程相关
- "technology" - 科技相关

### 方案 2：使用现有图片作为占位图

你可以暂时使用 `robocon.png` 作为所有项目的占位图：

```bash
cd mywebsite/static/images

# 复制 robocon.png 作为占位图
cp projects/robocon.png achievements/ieee-paper.jpg
cp projects/robocon.png achievements/robocon.jpg
cp projects/robocon.png achievements/competition.jpg
cp projects/robocon.png projects/fault-detection.jpg
```

然后在 `hugo.yaml` 中取消注释所有图片行。

### 方案 3：保持当前状态（推荐）

如果你不着急添加图片，可以保持当前状态：
- Robocon 项目有图片 ✅
- 其他项目暂时没有图片，显示默认样式
- 等有合适的图片后再添加

这样网站仍然可以正常显示，只是部分卡片没有图片而已。

---

## 🔍 验证图片路径

如果添加图片后仍然无法显示，检查以下几点：

1. **文件名是否完全匹配**
   - `hugo.yaml` 中：`/images/achievements/ieee-paper.jpg`
   - 实际文件：`static/images/achievements/ieee-paper.jpg`
   - 注意大小写和扩展名（.jpg vs .JPG）

2. **文件是否存在**
   ```bash
   ls -la static/images/achievements/
   ls -la static/images/projects/
   ```

3. **路径格式是否正确**
   - ✅ 正确：`/images/projects/robocon.png`
   - ❌ 错误：`static/images/projects/robocon.png`
   - ❌ 错误：`images/projects/robocon.png`（缺少开头的 `/`）

4. **图片是否已提交到 Git**
   ```bash
   git status
   git add static/images/
   ```

---

## 📋 快速检查清单

在部署前，确保：

- [ ] 所有图片文件都在正确的目录下
- [ ] 图片文件名与 `hugo.yaml` 中的配置完全匹配
- [ ] 已在 `hugo.yaml` 中取消注释相应的 `image:` 行
- [ ] 本地预览确认图片正确显示
- [ ] 图片文件已添加到 Git 并提交

---

## 🆘 常见问题

### Q: 为什么我添加了图片但网站上还是不显示？

A: 检查以下几点：
1. 确保图片文件已提交并推送到 GitHub
2. 确保 GitHub Actions 部署成功（查看 Actions 标签页）
3. 清除浏览器缓存后刷新
4. 检查浏览器控制台是否有 404 错误

### Q: 图片太大，加载很慢怎么办？

A: 使用图片压缩工具：
- **在线工具**: https://tinypng.com/ 或 https://squoosh.app/
- **命令行**: `convert input.jpg -quality 85 -resize 1200x output.jpg`

### Q: 我可以使用 PNG 格式吗？

A: 可以！只需确保 `hugo.yaml` 中的扩展名与实际文件匹配：
```yaml
image: /images/projects/robocon.png  # 如果文件是 .png
```

---

**现在你的网站可以正常显示了！** 🎉

等你准备好图片后，按照上面的步骤添加即可。

