# AstrBot Pixiv 搜索插件

[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/vmoranv-reborn/astrbot_plugin_pixiv_search)
[![文档](https://img.shields.io/badge/AstrBot-%E6%96%87%E6%A1%A3-blue)](https://astrbot.app)
[![aiohttp](https://img.shields.io/pypi/v/aiohttp.svg)](https://pypi.org/project/aiohttp/)

![:@astrbot_plugin_pixiv_search](https://count.getloli.com/get/@astrbot_plugin_pixiv_search?theme=booru-lewd)

这是一个为 [AstrBot](https://astrbot.app) 开发的 Pixiv 搜索插件，让你可以在聊天中轻松搜索和获取 Pixiv 插画作品。

## ✨ 核心特性

- 🎨 **多种搜索方式**: 支持标签搜索、用户搜索、作品详情查询
- 📚 **内容多样化**: 插画、小说、排行榜、推荐作品一应俱全
- 🎬 **动图支持**: 自动识别并转换 Pixiv 动图（ugoira）为GIF格式
- 🔍 **高级搜索**: 深度搜索、与搜索、相关作品推荐
- 🛡️ **内容控制**: 灵活的 R18 内容过滤配置
- ⚙️ **高度可配置**: 返回数量、显示详情、AI 作品过滤等
- 🔐 **安全管理**: 通过 WebUI 安全管理 API 凭据

## 🎯 主要功能

### 搜索功能
- `/pixiv <标签>` - 标签搜索插画
- `pixiv深度搜索 <标签>` - 深度搜索更多相关作品
- `pixiv搜索所有标签 <标签>` - 与搜索(同时包含所有标签)
- `pixiv搜索用户 <用户名>` - 搜索用户
- `pixiv搜索小说 <标签>` - 搜索小说
- `/pixiv下载小说并加密 <小说ID>` - 下载小说为 pdf 文件并用文件md5值进行加密

### 随机搜索功能
- `/pixiv随机搜索 <标签>` - 添加随机搜索标签
- `/pixiv列出随机搜索标签` - 列出当前随机搜索标签
- `/pixiv删除随机搜索标签 <序号>` - 删除指定序号的随机搜索标签
- `/pixiv暂停随机搜索` - 暂停当前群聊的随机搜索
- `/pixiv恢复随机搜索` - 恢复当前群聊的随机搜索
- `/pixiv查看随机搜索队列状态` - 查看随机搜索队列状态
- `/pixiv_random_force` - 强制执行当前群聊的随机搜索（调试用）

### 排除 tag
- `-<tag>` - 排除包含 `<tag>` 的插画(仅在 /pixiv, pixiv搜索小说, pixiv深度搜索, pixiv搜索所有标签 中有效)

### 内容获取
- `/pixiv推荐作品` - 获取推荐作品
- `/pixiv排行榜作品 [模式] [日期]` - 排行榜作品
- `/pixiv趋势标签` - 获取趋势标签
- `/pixiv获取大家的新插画作品 [类型] [最大作品ID]` - 获取大家的新插画作品
- `/pixiv获取大家的新小说 [最大小说ID]` - 获取大家的新小说
- `/pixiv获取推荐小说` - 获取推荐小说

### 详情查询
- `/pixiv指定作品详情 <作品ID>` - 指定作品详情（支持动图）
- `/pixiv用户详细 <用户ID>` - 用户详细信息
- `/pixiv相关作品推荐 <作品ID>` - 相关作品推荐
- `/pixiv小说系列详情 <系列ID>` - 小说系列详情
- `/pixiv特辑详情 <特辑ID>` - 特辑详情

### 评论功能
- `/pixiv获取作品评论 <作品ID> [偏移量]` - 获取作品评论
- `/pixiv获取小说评论 <小说ID> [偏移量]` - 获取小说评论

### 特殊功能
- `/pixiv是否展示AI作品 <设置>` - 设置是否展示AI生成作品

### 订阅功能
- `/pixiv订阅画师 <画师ID>` - 订阅画师
- `/pixiv_subscribe_add <画师ID>` - 订阅画师（旧命令兼容）
- `/pixiv取消订阅画师 <画师ID>` - 取消订阅画师
- `/pixiv_subscribe_remove <画师ID>` - 取消订阅画师（旧命令兼容）
- `/pixiv查看当前订阅列表` - 查看当前订阅列表
- `/pixiv_subscribe_list` - 查看当前订阅列表（旧命令兼容）

## 🚀 快速开始

### 前置条件

- Python >= 3.10
- 已部署的 AstrBot 实例 (v3.x+)
- 有效的 Pixiv 账号和 `refresh_token`

### 配置插件

1. 打开 AstrBot WebUI
2. 进入 `插件管理` -> 找到 Pixiv 搜索插件
3. 点击 `插件配置`，填写以下信息：
   - **Refresh Token**: 必填，用于 Pixiv API 认证
   - **R18 过滤模式**: 过滤R18/允许R18/仅R18
   - **返回图片数量**: 1-10张，默认1张
   - **AI作品显示**: 是否显示AI生成作品
   - **质量过滤**: 可选发送原画|大图|缩略图
   - **其他选项**: 详情显示、文件转发等

4. 保存配置

### 获取 Refresh Token

参考以下资源获取 Pixiv `refresh_token`:
- [pixivpy3 官方文档](https://pypi.org/project/pixivpy3/)
- [Pixiv OAuth 教程](https://gist.github.com/ZipFile/c9ebedb224406f4f11845ab700124362)

## 📝 使用示例

```bash
# 基础搜索
/pixiv 初音ミク,VOCALOID
/pixiv 茉莉安,-ntr

# 下载小说
/pixiv下载小说并加密 12345678

# 高级搜索  
pixiv深度搜索 原神,风景
pixiv搜索所有标签 初音ミク,可爱

# 获取推荐和排行榜
/pixiv推荐作品
/pixiv排行榜作品 daily

# 获取最新作品
/pixiv获取大家的新插画作品
/pixiv获取大家的新小说

# 小说相关
pixiv搜索小说 恋愛
/pixiv获取推荐小说
/pixiv小说系列详情 123456

# 评论功能
/pixiv获取作品评论 12345678
/pixiv获取小说评论 12345678

# 特殊功能
/pixiv是否展示AI作品 true

# 用户相关
pixiv搜索用户 某个画师名
/pixiv用户详细 123456

# 特辑功能
/pixiv特辑详情 123456

# 获取帮助
/pixiv_help

# 订阅功能
/pixiv订阅画师 123456
/pixiv取消订阅画师 123456
/pixiv查看当前订阅列表

# 随机搜索功能
/pixiv随机搜索 风景
/pixiv列出随机搜索标签
/pixiv删除随机搜索标签 1
/pixiv暂停随机搜索
/pixiv恢复随机搜索
/pixiv查看随机搜索队列状态
/pixiv_random_force
```

## ⚙️ 配置选项

| 配置项 | 说明 | 默认值 |
|--------|------|--------|
| `refresh_token` | Pixiv API 认证令牌 | 必填 |
| `return_count` | 每次搜索返回的图片数量 | 1 |
| `r18_mode` | R18内容处理模式 | 过滤 R18 |
| `ai_filter_mode` | AI作品显示设置 | 显示 AI 作品 |
| `deep_search_depth` | 深度搜索时搜索页数深度 | 3 |
| `show_details` | 是否在发送图片时附带详细信息 | true |
| `forward_threshold` | 是否启用消息转发功能（启用后所有图片都使用转发） | false |
| `show_filter_result` | 是否显示过滤内容提示 | true |
| `image_quality` | 默认发送的图片质量 (original/large/medium) | original |
| `is_fromfilesystem` | 是否通过文件转发 | false |
| `refresh_token_interval_minutes` | 自动刷新 Refresh Token 的间隔时间（分钟） | 180 |
| `subscription_enabled` | 是否启用订阅功能 | true |
| `subscription_check_interval_minutes` | 订阅更新检查间隔（分钟） | 30 |
| `proxy` | 网络代理地址，如 `http://127.0.0.1:7890` | 留空 |

## 🔧 故障排除

**SSL 错误**: 如遇到 `SSLError`，请更新 DNS 解析设置。参考: [SSLError 解决方案](https://github.com/upbit/pixivpy/issues/244)

**模块未找到**: 重启 AstrBot 以确保依赖正确安装

**API 认证失败**: 检查 `refresh_token` 是否有效和正确配置

## 📖 更多信息

- [AstrBot 官方文档](https://astrbot.app/)
- [插件开发指南](https://astrbot.app/develop/plugin.html)
- [问题反馈](https://github.com/vmoranv-reborn/astrbot_plugin_pixiv_search/issues)

## ⭐ 项目统计

<div align="center">

[![Star History Chart](https://api.star-history.com/svg?repos=vmoranv-reborn/astrbot_plugin_pixiv_search&type=Date)](https://star-history.com/#vmoranv-reborn/astrbot_plugin_pixiv_search&Date)

![Analytics](https://repobeats.axiom.co/api/embed/9e6727cd94536119069eebccfe45b505ac499470.svg "Repobeats analytics image")

</div>

## 📄 许可证

本项目遵循开源许可证，具体许可证信息请查看项目根目录下的 LICENSE 文件。

---

**注意**: 使用本插件需遵守 Pixiv 服务条款和相关法律法规。请合理使用 API 避免频繁请求。