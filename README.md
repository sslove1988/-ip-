# 公众号写作工作室 (Keke Bluegirl WeChat Studio)
# Keke WeChat Bluegirl Studio

> © 2026 孙可可 (keke). 本项目采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) 协议授权。
> 允许学习和交流使用，**禁止商业用途**，转载请注明原作者。
一个用于公众号文章创作与发布的 WorkBuddy/Codex Skill。

面向从未使用过的用户，一个 Skill 搞定公众号文章从写作、蓝衣女孩 IP 正文配图，到发布草稿箱的全流程。
它可以把一篇公众号文章从想法推进到：

## 特性
```text
选题 → 大纲 → 正文 → 标题 → 蓝衣女孩 IP 配图 → 排版 → 草稿箱准备
```

- **账号定位驱动**：首次使用填写 USER-PROFILE.md，AI 根据你的定位和风格写作
- **深度长文写作**：观点先行、案例论证、短句为主
- **蓝衣女孩 IP 配图**：内置配图指南，用 ImageGen 生成 Keke 蓝衣女孩 AI 工作流风格正文配图
- **小清新风格排版**：Optima-Regular 字体、蓝色主题、极简设计
- **图片清洗**：自动去灰底、去水印、平衡留白
- **一键发布**：自动清理旧草稿、上传封面、创建新草稿
- **自包含**：不依赖任何外部 Skill
## 核心功能

## 快速开始
- 写公众号文章初稿
- 优化标题和开头
- 为文章自动规划 3-5 张正文配图
- 使用 Keke 蓝衣女孩 IP 风格生成配图
- 整理成适合公众号后台复制的排版稿
- 在配置公众号 API 后，可准备发布到草稿箱

### 0. 安装 Python（如已安装可跳过）
## 配图风格

本 Skill 需要 **Python 3.10+**。打开终端输入 `python --version` 检查：
默认配图风格是：

- **已安装 3.10+** → 跳到第 1 步
- **未安装或版本过低** → 去官网下载：https://www.python.org/downloads/
  - Windows 安装时务必勾选 **"Add Python to PATH"**
  - macOS 推荐用 Homebrew：`brew install python@3.12`
- 蓝色卫衣女孩
- AI 机器人气泡
- 亮蓝 + 亮黄 + 黑色粗手写
- 白底贴纸感
- 每张图只讲一个核心意思
- 更像正文插图，不是封面海报

### 1. 安装 Skill
参考图放在：

将本目录放到 WorkBuddy 的 skills 目录：

```bash
# macOS / Linux
cp -r keke-wechat-bluegirl-studio ~/.workbuddy/skills/

# Windows
xcopy /E /I keke-wechat-bluegirl-studio %USERPROFILE%\.workbuddy\skills\keke-wechat-bluegirl-studio
```text
assets/ip-references/
```

### 2. 一键环境检查（推荐）
配图规则在：

```bash
python scripts/setup.py
```text
references/illustration-guide.md
```

脚本会自动检查 Python 版本、安装依赖（Pillow, numpy）、引导填写配置。
## 使用方式

> 如果 setup.py 运行失败，可手动安装依赖：
> ```bash
> pip install -r requirements.txt
> ```
把整个目录放到你的 skills 目录后，在 WorkBuddy/Codex 里说：

### 3. 配置账号

复制模板并填写：

```bash
cp USER-PROFILE-TEMPLATE.md USER-PROFILE.md
cp assets/wechat_config.template.json assets/wechat_config.json
```text
Use $keke-wechat-bluegirl-studio 帮我写一篇公众号文章，并配 3-5 张蓝衣女孩风格正文图。
```

在 `USER-PROFILE.md` 中填写：
首次使用前，复制并填写：

- 账号定位（你是谁、做什么）
- 目标用户
- 表达风格
- 微信公众号信息（AppID、AppSecret）
- 配图偏好（默认蓝衣女孩 IP 正文配图）
```text
USER-PROFILE-TEMPLATE.md → USER-PROFILE.md
assets/wechat_config.template.json → assets/wechat_config.json
```

### 4. 开始使用

在 WorkBuddy 中说：

> 帮我写一篇关于 XXX 的公众号文章，并配 3-5 张图

AI 会自动完成：写作 → 蓝衣女孩正文配图 → 清洗 → 排版 → 发布到草稿箱。
如果只是写文章和配图建议，可以先不填写公众号 API。

## 文件结构

```text
keke-wechat-bluegirl-studio/
├── SKILL.md                          # 主流程
├── USER-PROFILE-TEMPLATE.md          # 账号定位模板
├── USER-PROFILE.example.md           # 示例
├── requirements.txt                  # Python 依赖
├── .gitignore
├── agents/
│   └── openai.yaml                   # Codex/WorkBuddy 展示元信息
├── scripts/
│   ├── setup.py                      # 一键环境检查
│   ├── wechat_template.py            # 小清新排版引擎
│   ├── wechat_publish.py             # 发布脚本
│   ├── process_images.py             # 图片清洗
│   └── upload_user_image.py          # 用户图片上传
├── SKILL.md
├── USER-PROFILE-TEMPLATE.md
├── USER-PROFILE.example.md
├── assets/
│   ├── wechat_config.template.json   # 配置模板
│   └── ip-references/                # 蓝衣女孩 IP 参考图
└── references/
    ├── illustration-guide.md         # 蓝衣女孩 IP 正文配图完全指南
    ├── writing-style-guide.md        # 写作风格指南
    ├── template-schema.md            # 文章 JSON 格式
    └── wechat-api.md                 # API 避坑
│   ├── ip-references/
│   └── wechat_config.template.json
├── references/
│   ├── illustration-guide.md
│   ├── writing-style-guide.md
│   ├── template-schema.md
│   └── wechat-api.md
└── scripts/
    ├── process_images.py
    ├── setup.py
    ├── upload_user_image.py
    ├── wechat_publish.py
    └── wechat_template.py
```

## 许可证
## 注意

本项目采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)（署名-非商业性使用）协议。
- `USER-PROFILE.md` 和 `assets/wechat_config.json` 是私人配置，不要上传到公开仓库。
- 本 Skill 只准备草稿箱，不自动正式发布文章。
- 使用微信公众号 API 前，请确认 AppID、AppSecret 和 IP 白名单配置正确。

- ✅ 允许学习、交流、引用、修改
- ✅ **必须署名**：© 2026 孙可可 (keke)
- ❌ **禁止商业用途**
- ❌ 禁止闭源再发行
## License

CC BY-NC 4.0  
© 2026 孙可可 (keke)
