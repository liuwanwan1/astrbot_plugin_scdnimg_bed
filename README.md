# scdn 图床插件

基于 [img.scdn.io](https://img.scdn.io) API 的 AstrBot 图床插件，支持上传图片、通过 URL 上传以及查询图片公开元数据。

## 功能

- `/图床上传`：上传图片到 scdn 图床，支持附带图片、回复/引用图片消息或提供图片 URL
- `/图床链接`：通过远程图片 URL 上传
- `/图床查询`：查询图片公开元数据，支持直接传入 scdn 图片 URL
- `/图床解析`：解析 scdn 图片链接并将图片发送到群里
- `/图床帮助`：显示帮助信息

## 安装

1. 下载插件压缩包 `astrbot_plugin_scdnimg_bed.zip`
2. 在 AstrBot 插件管理页面上传并安装
3. 重载插件或重启 AstrBot

## 配置

在 AstrBot 插件配置界面中修改以下项：

| 配置项 | 说明 | 默认值 |
|--------|------|--------|
| `api_base_url` | 图床 API 基础地址 | `https://img.scdn.io/api/v1.php` |
| `default_cdn_domain` | 默认 CDN 域名 | `img.scdn.io` |
| `default_storage` | 默认存储位置（`local` / `telegram` / `r2`） | `local` |
| `default_output_format` | 默认输出格式 | `auto` |
| `timeout` | 请求超时时间（秒） | `60` |

## 命令用法

### 上传图片

```
/图床上传 [图片URL] [--format=webp] [--cdn=img.scdn.io] [--storage=local] [--password=密码]
```

- 直接附带图片
- 回复/引用一条图片消息（支持 aiocqhttp/QQ、Telegram 等常见平台）
- 提供图片 URL（支持 HTTP/HTTPS、本地文件路径以及 base64 data URI）

示例：

```
/图床上传 https://example.com/image.png --format=webp --storage=r2
```

### 通过 URL 上传

```
/图床链接 <图片URL> [--format=webp] [--cdn=img.scdn.io] [--storage=local]
```

示例：

```
/图床链接 https://example.com/image.png --format=webp
```

### 查询图片

```
/图床查询 <图片ID或文件名>
/图床查询 <scdn图片URL>
```

支持直接传入 scdn 图片 URL，插件会自动提取文件名进行查询。

示例：

```
/图床查询 abc123.png
/图床查询 https://img.scdn.io/i/abc123.png
```

## 可用参数

- `--format`：输出格式，可选 `auto`、`jpg`、`jpeg`、`png`、`webp`、`gif`、`webp_animated`
- `--cdn`：CDN 域名
- `--storage`：存储后端，可选 `local`、`telegram`、`r2`
- `--password`：为图片设置访问密码

## 解析 scdn 链接并发图

```
/图床解析 <scdn图片URL>
```

示例：

```
/图床解析 https://img.scdn.io/i/abc123.png
```

机器人会查询图片元数据，并把图片发回群里。

## 命令别名

| 命令 | 别名 |
|------|------|
| `/图床上传` | `/上传图床`、`/scdn-upload` |
| `/图床链接` | `/上传图床链接`、`/scdn-url` |
| `/图床查询` | `/查询图床`、`/scdn-info` |
| `/图床解析` | `/解析图床`、`/scdn-parse`、`/scdn-send` |
| `/图床帮助` | `/scdn-help` |

## 依赖

本插件仅依赖 AstrBot 内置 API，无需额外安装依赖。

## 作者

Clove.
