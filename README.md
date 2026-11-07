# mysthub · 永不落幕的推理盛宴

一站式推理文娱自留地，收录 152 部小说、电影、游戏与动漫。

在线地址：[https://jiuhaonanyan.github.io/mysthub/](https://jiuhaonanyan.github.io/mysthub/)

打开 `index.html` 即可本地体验，HTML/CSS/JS 在此文件内。请保留同目录的 `assets/covers/`：作品真实配图是本地资源。无需构建或服务器，支持离线运行。

## GitHub Pages 发布

在仓库的 **Settings → Pages** 中选择 **Deploy from a branch**，分支为 **main**、目录为 **/(root)**。仓库包含 `.nojekyll`，GitHub 会直接发布静态文件。以后推送到 `main` 的修改会自动触发重新发布。

## 本轮变化

- 序章展墙：鼠标目标位移范围由约 22×16px 扩为 260×180px，保留惯性；拖动和滚轮位移也扩大。
- 首页底部三分之一区域：鼠标／触摸轨迹驱动不规则墨迹揭露，支持重置。
- 偏好匹配背景：参考 Griflan Labs 的球面网格，用本地推理作品封面构成缓慢旋转的曲面图集，支持鼠标视差、暂停和减弱动画；前景内容按 75% 缩放。
- 偏好匹配：左侧自由选三个标签；右侧墨迹刮开随机小说，每次进入或同标签页刷新都会避开上一本。可直接揭晓。
- 作品库：152 部，其中小说 100、电影／剧集 25、游戏 25、动漫 2；三津田信三 16 部。
- 作品档案：实际纹理加载进度、原生 WebGL 空心厚壁圆柱（内外壁、环形端面、倒角）、加载后约 2.5 秒的俯视到正视动画、与主体保持间距的镜像倒影；三个入口为小说、游戏、电影。电影入口含动漫子筛选。
- 分类展览：大图居中的纵向排列、横向浏览切换、来源链接、搜索和三津田信三快捷筛选。
- 收藏、状态与手记保存在浏览器本地。

## 资源与维护

- `data/catalog-150.json`：可编辑数据副本（文件名沿用旧版，当前共 152 部）；修改后需同步 `index.html` 内 WORKS（页面为方便双击运行而使用内联数据）。
- `data/cover-sources.json`：152 张真实封面／海报的原始链接、条目链接、匹配标题及来源记录。
- `assets/covers/`：本地封面文件。图片对应所列版本，可能与其他版本的出版封面不同。
- `assets/match/cover-atlas.jpg`：偏好匹配背景使用的 50 张作品封面图集，包含本次补充的游戏。`index.html` 内的 MATCH_ATLAS_IDS 与 MATCH_ATLAS_TEXTURE 保存图集顺序和内嵌副本，支持直接打开 HTML。
- 圆柱首屏使用三张分类配图：`assets/archive/literature.jpg`（小说）、`assets/archive/games.jpg`（游戏）、`assets/archive/cinema.jpg`（电影）。图片同时内嵌在 `index.html` 的 ARCHIVE_TEXTURES 中，并在 `data/cylinder-textures.js` 保留副本，以支持 `file://` 模式的 WebGL 纹理；更换配图时需同步这三处。其余作品封面懒加载本地文件。
- 历史版本与打包副本仅留在本地，由 `.gitignore` 排除。

## 参考与实现范围

背景运动参考 https://labs.griflan.com/ 的球面图集，使用本地作品封面独立实现。研究了 https://yuenye.com/works/ 的墨迹内容揭露，以及 https://aikawakenichi.com/ 的加载过程、图像圆柱、反射和作品排列。当前是独立实现的对应交互；未复制原站的摄影素材、专有字体或打包代码。不是逐像素复刻，也未复用原站的折射着色器。

## 已验证

Chrome 桌面与触屏模拟、320/390/768/1440px，无外网环境；152 张图片解码；三标签匹配、刮书切换、圆柱键盘与按钮操作、三个分类、纵横展览、筛选搜索、收藏状态手记持久化、减弱动画、无 WebGL 回退。真实设备帧率需按设备进一步观察。
