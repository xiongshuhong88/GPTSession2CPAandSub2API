# ChatGPT Session to CPA / sub2api

纯前端单页面工具，用来把 ChatGPT Web 登录 session JSON 转换成 CPA 或 sub2api 可导入 JSON。

## 在线使用

### [**》》 点我直接使用 《《**](https://gtxx3600.github.io/GPTSession2CPAandSub2API/)

## 使用提示

Plus 号可以用此方式导入中转站使用；Free 号的 access token 不能用于调用接口。

## 支持输入

支持粘贴或拖入 ChatGPT Web session JSON，例如包含：

- `user.email`
- `accessToken`
- `sessionToken`
- `expires`
- `account.id`
- `account.planType`

页面也会尝试从 `accessToken` 的 JWT payload 中补充邮箱、账号 ID、用户 ID、计划类型和过期时间。

## 输出格式

- `CPA`：生成 Codex CPA auth JSON，包含 `type: "codex"`、`access_token`、`session_token`、`id_token`、`email`、`account_id`、套餐和过期时间等字段；缺少真实 `id_token` 时会根据 session 与 access token claims 构造 CPA 可解析的占位 claims。
- `sub2api`：生成参考 `CPA2sub2API` 项目的 `exported_at/proxies/accounts` 结构，账号平台为 `openai`，类型为 `oauth`。
ChatGPT Web session 通常不包含 CPA OAuth 文件里常见的 `refresh_token`，因此 access token 过期后不能自动刷新。

## 本地使用

直接打开：

```text
docs/index.html
```

所有解析和转换都在浏览器本地完成，不上传 token，不写入本地存储。
