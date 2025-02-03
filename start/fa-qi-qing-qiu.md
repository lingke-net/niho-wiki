---
icon: webhook
---

# 发起请求

您可以将以下命令粘贴到终端中以运行您的第一个API请求。请确保将 `$OPENAI_API_KEY` 替换为您的 API 密钥。

{% code title="CMD" overflow="wrap" lineNumbers="true" %}
```python
curl {请前往“API接口列表”查看API地址}
  -H "Content-Type: application/json"
  -H "Authorization: Bearer $OPENAI_API_KEY"
  -d '{ "model": "gpt-3.5-turbo", "messages": [{"role": "user", "content": "Say this is a test!"}], "temperature": 0.7 }'
```
{% endcode %}

此请求查询`gpt-3.5-turbo`模型，以完成以提示符“ _Say this is a test_ ”开头的文本。您应该会收到一个类似于以下内容的响应：

{% code title="JSON" overflow="wrap" lineNumbers="true" %}
```json
{
 "id":"chatcmpl-abc123",
 "object":"chat.completion",
 "created":1677858242,
 "model":"gpt-3.5-turbo-0301",
 "usage":{ "prompt_tokens":13,
  "completion_tokens":7, 
  "total_tokens":20
  }, 
  "choices":[{"message":{"role":"assistant","content":"This is a test!"}, "finish_reason":"stop","index":0}]}
```
{% endcode %}

现在您已经生成了第一个聊天完成。我们可以看到`finish_reason`是`stop`，这意味着API返回了模型生成的完整完成。在上面的请求中，我们只生成了一个单独的消息，但您可以设置`n`参数以生成多个消息选项。

在此示例中，`gpt-3.5-turbo`被用于更传统的文本补全任务。该模型还针对[聊天应用程序](https://www.openaidoc.com.cn/docs/guides/chat)进行了优化。
