好的！以下是完整的操作指南，包含从GitHub克隆到本地(WSL)、日常修改和提交的全流程：

### 1️⃣ 克隆仓库到WSL
```bash
# 进入你常用的开发目录（示例）
cd ~/dev

# 克隆仓库（替换你的GitHub用户名）
git clone https://github.com/你的用户名/CommentZoneSurfer.git

# 进入项目目录
cd CommentZoneSurfer

# 创建Python虚拟环境（推荐）
python -m venv .venv
source .venv/bin/activate  # 激活环境

# 安装依赖（如果有requirements.txt）
pip install -r requirements.txt
```

### 2️⃣ 日常开发修改流程
#### 修改代码后提交：
```bash
# 查看改动状态
git status

# 添加所有修改文件（或指定文件）
git add .

# 提交修改（建议描述清晰）
git commit -m "feat: 新增弹幕转译功能"

# 推送到GitHub
git push origin main
```

#### 如果需要同步远程修改：
```bash
# 拉取远程最新代码
git pull origin main

# 如果有冲突，解决后执行：
git add .
git commit -m "解决合并冲突"
git push
```

### 3️⃣ 推荐开发环境配置
```bash
# 安装VS Code（如果尚未安装）
sudo apt update && sudo apt install code

# 在项目目录中启动VS Code
code .

# 推荐安装的VS Code插件：
- Python
- Pylance
- GitLens
- WSL (Remote - WSL)
```

### 4️⃣ 项目结构建议调整
```
CommentZoneSurfer/
├── .gitignore         # 忽略虚拟环境等文件
├── README.md          # 项目说明
├── requirements.txt   # 依赖列表
├── config/
│   └── settings.json  # 配置文件
├── src/
│   ├── crawler.py     # 爬虫主逻辑
│   ├── analyzer.py    # 评论分析
│   └── generator.py   # 攻略生成
└── outputs/           # 生成的攻略
```

### 5️⃣ 常用命令速查表
| 操作 | 命令 |
|-------|-------|
| 查看分支 | `git branch -v` |
| 创建新功能分支 | `git checkout -b feature/xxx` |
| 合并分支 | `git merge feature/xxx` |
| 撤销本地修改 | `git checkout -- <file>` |
| 查看提交历史 | `git log --oneline --graph` |

### ⚠️ 注意事项
1. 修改前先拉取最新代码：`git pull`
2. 重要功能开发建议新建分支
3. 提交前运行测试（如果有）
4. API密钥等敏感信息不要提交，添加到`.gitignore`

### 🛠️ 首次设置可能需要的WSL配置
```bash
# 设置Git身份（只需一次）
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"

# 如果需要SSH连接GitHub
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub  # 然后复制到GitHub SSH Keys设置
```