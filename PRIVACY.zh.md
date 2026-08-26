# CISpir 隐私政策

**最后更新：2026 年 8 月**

CISpir 没有后端服务器，也不在自己的服务器上收集用户数据。本页如实说明扩展会存储和发送哪些数据。

## 保留在你设备上的数据

- **字幕文本、音频片段和视频元数据**仅通过 AnkiConnect（`localhost:8765`）发送到你本地的 Anki，不会离开你的电脑。
- **设置与偏好**——包括 Anki 牌组名称、当前标签页 ID、打赏状态和 AI 结果缓存——均通过 Chrome 的 `storage.local` API 存储在本地。
- **API 密钥**在存储到 `storage.local` 前会先经过 AES-GCM 加密。

## 发送给 AI 服务商的数据

使用 AI 功能（翻译、语法分析、查词、视频摘要）时，字幕文本或选中的句子会**从你的浏览器直接**发送给你所配置的 AI 服务商（OpenAI、Anthropic、Google AI 或 DeepSeek）。CISpir 中间没有服务器，请求由你的 API 密钥授权。若未配置密钥或未使用这些功能，则不会发送任何数据。

## 匿名用量统计（可选，默认关闭）

扩展内置一个可选的匿名用量统计（Google Analytics 4）。它**默认关闭**，仅当发布者配置了统计 ID 后才会启用。启用后仅发送聚合的、非个人化的事件，例如安装/更新、每日活跃和功能使用——使用随机生成的标识符，不进行指纹识别，也绝不会发送你的字幕文本或账号信息。

## 第三方服务

CISpir 不集成任何广告或跟踪服务。

## 联系方式

如有问题，请在 [github.com/smith0814666/CISpir-anki-extenstion](https://github.com/smith0814666/CISpir-anki-extenstion) 提交 Issue。
