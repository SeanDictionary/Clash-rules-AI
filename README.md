# Clash-rules-AI

本仓库专用于存放与 AI 平台相关的 Clash 分流规则集。部分 AI 平台对地区限制较为严格，即使使用部分节点仍可能无法访问，因此需要更精准的规则来识别和分流这些平台的流量。本仓库的规则集旨在帮助用户更好地匹配并规避 AI 平台的特殊地区限制。

## 适用场景

- 访问如 OpenAI、Google AI、Anthropic、Copilot 等对地区和 IP 检查敏感的 AI 平台；
- 某些普通节点无法访问特定 AI 平台服务时，通过本规则集帮助精准识别与分流；
- 只需专门维护和更新 AI 平台规则，便于自定义和日常维护。

## 使用方法

在 Clash/Yacd/Neko 等客户端的配置文件中引入以下内容即可：

```yaml
rule-providers:
  ai-sensitive:
    type: http
    behavior: domain
    format: yaml
    url: "https://cdn.jsdelivr.net/gh/SeanDictionary/Clash-rules-AI@main/ai-strict.yaml"
    path: ./ruleset/ai-sensitive.yaml
    interval: 86400
```

或者，也可以直接使用 GitHub Raw 链接：

```yaml
rule-providers:
  ai-sensitive:
    type: http
    behavior: domain
    format: yaml
    url: "https://raw.githubusercontent.com/SeanDictionary/Clash-rules-AI/main/ai-strict.yaml"
    path: ./ruleset/ai-sensitive.yaml
    interval: 86400
```

然后在 `rules` 部分添加对该规则集的调用，例如：

```yaml
rules:
  - RULE-SET,ai-sensitive,PROXY
  # 其他规则...
```

## 规则集说明

- `ai-strict.yaml`：收录有严格地区限制的AI平台及其相关的域名；
- 规则源会不定期维护，接受PR
