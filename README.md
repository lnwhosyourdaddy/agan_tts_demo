# 壹鸽 TTS · 音色试听平台

对外展示用的音色试听工具，收录三套音色模型共 **216 款音色**，全部音频已本地化，无需登录、可离线访问。

## 一、目录结构

```
├── index.html          # 单页应用（约 42 KB）
├── assets/
│   ├── logo.png        # 品牌标识
│   └── favicon.png
├── audio/              # 216 个音色音频（MP3，约 15 MB）
├── .gitignore
└── README.md
```

**总计约 15 MB**，适合 GitHub Pages 托管。

## 二、三套音色模型

| 模型 | 音色数 | 计费 | 定位 |
|---|---|---|---|
| **标准版** | 101 | **不额外收费**（当前方案在用） | 通用、客服、方言等常用场景 |
| **进阶版** | 67 | 需额外收费（资费请联系商务） | 高品质与智能对话音色 |
| **旗舰版** | 48 | 需额外收费（资费请联系商务） | 方言与多语种音色 |

页面顶部对两类计费方式有明确标注，客户可据此判断选用哪套模型。

## 三、部署到 GitHub Pages

```bash
cd tts-试听平台
git init
git add .
git commit -m "壹鸽 TTS 音色试听平台"

git remote add origin https://github.com/<账号>/<仓库名>.git
git branch -M main
git push -u origin main
```

仓库 → **Settings → Pages**：
- Source：`Deploy from a branch`
- Branch：`main` / `/ (root)`
- 保存后约 1–2 分钟生效

访问：`https://<账号>.github.io/<仓库名>/`

## 四、使用说明

- 点击「试听」即播放，无需登录
- 同一时间只播放一个音色，切换自动停止上一个
- 每款音色下方展示其音频文本内容（部分为官方演示样音）
- 支持按模型、性别、类型筛选，以及名称搜索

## 五、对外展示前请确认

1. 页面内不含任何上游供应商名称（已做全量脱敏检查）
2. `index.html` 与 `assets/` 不含密钥（合成脚本与密钥均在本机独立目录，不纳入本仓库）
3. 音频为演示样音；对外演示前建议用实际业务话术再合成一版
4. 商务联系方式：`index.html` 中 `mailto:sales@example.com` 需替换为真实邮箱

## 六、重新生成音频（内部操作）

音频合成脚本与密钥存放在本机 `/Users/ganyuning/Documents/1-test/0-tts/`，**不纳入本仓库**。

如需更换演示文本或补充音色：

```bash
# 1. 修改合成脚本中的 TEXT 变量
# 2. 清空旧音频后重新合成
# 3. WAV 转 MP3：ffmpeg -i in.wav -codec:a libmp3lame -b:a 48k -ar 16000 -ac 1 out.mp3
# 4. 重新生成页面与数据
```

> 演示文本请使用**与具体业务无关的中性句子**，避免在对外页面中出现客户项目信息。