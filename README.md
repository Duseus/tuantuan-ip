# 貉团团 · Tuantuan IP Kit

> 团成一团，慢慢向前。

站点吉祥物「**貉团团**」的完整形象资产库 —— Q 版萌系貉，二头身，城市夜行干饭团子。
所有图片、动画与矢量工程源统一收拢在此，Git 版本管理，可追溯、可校验、可复用。

## 目录结构

```
tuantuan-ip/
├── characters/            定稿角色图
│   ├── hero.png                 704K 主形象
│   ├── hello / joy / love / cheer / thanks / sad
│   │   wow / thinking / coffee / work / rest / wander
│   │                            十二种情绪，1024×1024 透明底 PNG
│   └── expressions-green/       19 张绿幕表情（angry / base / cry / eat / fight
│                                happy / huh / hungry / love / night / ok / peek
│                                please / proud / relax / run / shock / sleepy / wave）
├── stickers/              十二情绪表情贴纸，512×512 透明底 PNG
├── views/                 front / three-quarter / side / back 四视角
├── avatars/
│   ├── cream / pink / sage / lilac     四种配色头像，800×800
│   ├── blog/                           博客站头像 8 张（blog_av_* + square）
│   ├── github/                         GitHub 头像 2 张
│   └── avatar_reading / milktea / coding / gaming
│       sleepy / thumbsup               2026-11 新增主题头像 6 张，1024×1024
├── wallpapers/            phone-day / phone-night 1080×1920，desktop 2560×1440
├── banners/               blog-cover 1920×640，social-card 1200×630
├── boards/                设定图：character-sheet 2400×1600，expressions 2400×1800，
│                          plus main_v1 / milktea_v1 / turnaround_v1 / stickers_v1-v2
├── brand/                 emblem / wordmark / pattern / original-character 四枚 SVG
├── animations/
│   ├── gif/                        20 个动态表情 GIF
│   └── mp4/                        gs_* 绿幕动画 6 支、sc_* 场景动画 3 支、
│                                   tuantuan_wave / _v2 挥手动画
├── source/                矢量工程源（Lottie / Bodymovin）
├── docs/character-bible.md          角色设定、形态规范、标准色板
├── manifest.json                    IP Kit v2.1 文件清单，含 sha256 校验
└── preview.html                     本地素材库预览页
```

## 快速使用

```bash
# 克隆
git clone https://github.com/Duseus/tuantuan-ip.git

# 校验文件完整性（对照 manifest.json 的 sha256）
python3 - <<'PY'
import hashlib, json, pathlib
root = pathlib.Path('.')
bad = []
for item in json.loads((root/'manifest.json').read_text())['files']:
    p = root/item['file']
    if not p.exists():
        continue                      # 清单按 ip/ 原始结构记录，部分已重新归档
    h = hashlib.sha256(p.read_bytes()).hexdigest()
    if h != item['sha256']:
        bad.append(item['file'])
print('校验不一致:', bad or '无')
PY
```

## 角色一致性

新增形象请以 `docs/character-bible.md` 的**形态规范**与**标准色板**为准，形态特征不可改动，只追加动作、道具、场景。

形象的生产管线（生图工具、脚本与方法）不在本仓库公开范围内，另行私有管理。

## 版权

貉团团形象、命名及相关视觉资产版权归 **Duseus / 山川行貉** 所有，保留所有权利。
转载请注明出处。如需授权使用，请先联系。
