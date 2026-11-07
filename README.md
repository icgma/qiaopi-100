# 侨批为证 · 精选一百件（qiaopi-100）

《侨批为证：一封批里的家国天下》项目面向全网开放的精选展示站。从一万件冻结正典中
按信、家、国、天下四个维度各选二十五件，原件影像、识读文本、四维解读三层并陈。

## 内容

- `index.html`：站点页面（自包含，无外部依赖；数据经 `data/items.json` 加载）
- `data/items.json`：100 件选目与逐页识读（含字段、戳记、清晰度）
- `images/<ssno>/pN.jpg`：原件影像降采样副本（宽 1000px，JPEG q82，共约 49MB）

## 选件规则（可复现）

脚本：`../mining/scripts/site100_build.py`（仓库根运行 `python pandeng2027/mining/scripts/site100_build.py`）。
配额：信 25／家 25／国 25／天下 25；清晰度（legibility）≥3，优先高者；钉选经典件
（再成信局「專收銀信 保家回唐」、祥泰隆、林家簇、金圆券件等）；同批局限 3 件、同称谓限 8 件防扎堆。

## 口径

- 底本：汕头大学图书馆藏、CADAL 数字化侨批扫描档案；实收唯一 48,830 件，冻结正典 10,000 件（22,974 页）。
- 识读：大模型批量＋人工校读双线；2,802 件另有人工全文识读对照。不确定处以（？）与 □ 标注。
- 版权：馆藏数字化影像（含水印）仅作学术展示；另行使用请联络馆藏方。

## 技术体制（给接手优化的 LLM）

- **形态**：纯静态站，零框架、零构建、零 CDN 依赖。无后端、无数据库、无打包器。
- **页面**：`index.html` 单文件自包含（内联 CSS＋vanilla JS，约 300 行）。数据经 `fetch('data/items.json')` 加载后前端渲染。
- **数据**：`data/items.json`（100 件，含逐页 transcript／fields／stamps／legibility）；由 `../mining/scripts/site100_build.py` 从冻结正典自动生成，**改数据重跑脚本，不手编 JSON**。
- **图片**：`images/<ssno>/pN.jpg`，原件降采样副本（宽 1000px、JPEG q82，约 49MB／244 张）；卡片用 `loading="lazy"`。
- **托管**：GitHub Pages（仓库 icgma/qiaopi-100，main 分支根目录）。重新发布＝推 main 即自动构建。
- **交互现状**：四维筛选 tab、检索（题签/编号/批局）、卡片网格、详情弹层（原件页码切换＋识读/字段两 tab＋前后件导航，支持 Esc 与左右方向键）。
- **可选优化方向**：图片 srcset 或 AVIF 再压；检索升级为拼音/繁简兼容；详情层同户多件并排对比；无障碍（alt、键盘焦点环）；schema.org 结构化数据与 SEO 元信息。

## 部署

GitHub Pages，仓库 icgma/qiaopi-100，线上地址 https://icgma.github.io/qiaopi-100/ 。
重新发布＝把本目录内容推到仓库 main 分支（Pages 自动构建）；本机部署副本在 `%TMP%/qiaopi-100-deploy`（gh 当前活动账户是 icgma）。

## 部署记录

- 2026-11-08 首发版上线（100 件，四维各 25；Pages 构建通过，浏览器双页验收通过）。
