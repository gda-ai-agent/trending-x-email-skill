---
name: trending-x-email
description: 查询 X.com (Twitter) 最近24小时最火的10个话题，并通过邮件发送报告。使用场景：(1) 用户想要获取 X 热门话题 (2) 用户想要定期收到热门趋势邮件 (3) 用户指定了 X 作为信息来源
---

# Trending X Email Skill

获取 X.com 最近24小时最火的10个话题，并通过邮件发送报告。

## 工作流程

### 1. 搜索热门话题

使用 web_search 搜索 X.com trending：

```
Query: "X.com trending today" 或 "Twitter trending 2024"
Freshness: pd (past day)
```

### 2. 获取详细信息

对每个热门话题，使用 web_fetch 或 browser 获取更多详情。

### 3. 发送邮件

使用 message 工具发送邮件：

```json
{
  "action": "send",
  "channel": "email",
  "target": "web3school@outlook.com",
  "subject": "X.com 热门话题 TOP 10 (最近24小时)",
  "message": "邮件正文..."
}
```

## 邮件模板

```markdown
# 🔥 X.com 热门话题 TOP 10

**更新时间**: {datetime}

---

## 1. {topic1}
- 热度: {metrics}
- 简介: {description}
- 链接: {url}

## 2. {topic2}
...

---

由 AI 自动生成
```

## 配置

如需修改收件人，在使用时指定邮箱地址。

## 依赖

- web_search: 搜索热门话题
- web_fetch: 获取话题详情
- message: 发送邮件
