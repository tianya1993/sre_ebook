# wrk

## 1. wrk 介绍

压测工具

### 1.2 POST 方法

```lua
vi   post.lua
wrk.method = "POST"
wrk.body = "{\"UUID\":\"96a940e6-ada5-4e13-9efb-e444610240cf\",\"ip\":\"195.16.186.34\"}"
wrk.headers["Content-Type"] = "application/json"
response = function(status, headers, body)

```
