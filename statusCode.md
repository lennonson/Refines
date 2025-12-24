## ✅ 1xx：信息性状态码（Informational）

| 状态码 | 含义                                |
| ------ | ----------------------------------- |
| 100    | Continue（继续）                    |
| 101    | Switching Protocols（切换协议）     |
| 102    | Processing（正在处理，WebDAV 扩展） |
| 103    | Early Hints（早期提示）             |



------

## ✅ 2xx：成功状态码（Success）

| 状态码 | 含义                                        |
| ------ | ------------------------------------------- |
| 200    | OK（请求成功）                              |
| 201    | Created（已创建）                           |
| 202    | Accepted（已接受，尚未处理）                |
| 203    | Non-Authoritative Information（非授权信息） |
| 204    | No Content（无内容）                        |
| 205    | Reset Content（重置内容）                   |
| 206    | Partial Content（部分内容）                 |
| 207    | Multi-Status（多状态，WebDAV）              |
| 208    | Already Reported（已报告，WebDAV）          |
| 226    | IM Used（IM 已使用）                        |



------

## ✅ 3xx：重定向状态码（Redirection）

| 状态码 | 含义                             |
| ------ | -------------------------------- |
| 300    | Multiple Choices（多种选择）     |
| 301    | Moved Permanently（永久移动）    |
| 302    | Found（临时移动）                |
| 303    | See Other（查看其它位置）        |
| 304    | Not Modified（未修改）           |
| 305    | Use Proxy（使用代理，已废弃）    |
| 307    | Temporary Redirect（临时重定向） |
| 308    | Permanent Redirect（永久重定向） |



------

## ✅ 4xx：客户端错误（Client Error）

| 状态码 | 含义                                          |
| ------ | --------------------------------------------- |
| 400    | Bad Request（错误请求）                       |
| 401    | Unauthorized（未授权）                        |
| 402    | Payment Required（需要付款，保留状态码）      |
| 403    | Forbidden（禁止访问）                         |
| 404    | Not Found（资源未找到）                       |
| 405    | Method Not Allowed（方法不允许）              |
| 406    | Not Acceptable（不可接受）                    |
| 407    | Proxy Authentication Required（需要代理授权） |
| 408    | Request Timeout（请求超时）                   |
| 409    | Conflict（冲突）                              |
| 410    | Gone（已删除）                                |
| 411    | Length Required（需要内容长度）               |
| 412    | Precondition Failed（前提条件失败）           |
| 413    | Payload Too Large（请求体太大）               |
| 414    | URI Too Long（URI 太长）                      |
| 415    | Unsupported Media Type（不支持的媒体类型）    |
| 416    | Range Not Satisfiable（请求范围不满足）       |
| 417    | Expectation Failed（预期失败）                |
| 418    | I'm a teapot（我是一个茶壶，彩蛋）            |
| 422    | Unprocessable Entity（不可处理的实体）        |
| 426    | Upgrade Required（需要升级）                  |
| 429    | Too Many Requests（请求太多）                 |



------

## ✅ 5xx：服务器错误（Server Error）

| 状态码 | 含义                                             |
| ------ | ------------------------------------------------ |
| 500    | Internal Server Error（服务器内部错误）          |
| 501    | Not Implemented（未实现）                        |
| 502    | Bad Gateway（错误网关）                          |
| 503    | Service Unavailable（服务不可用）                |
| 504    | Gateway Timeout（网关超时）                      |
| 505    | HTTP Version Not Supported（不支持的 HTTP 版本） |
| 507    | Insufficient Storage（存储空间不足，WebDAV）     |
| 508    | Loop Detected（检测到循环）                      |
| 510    | Not Extended（未扩展）                           |
| 511    | Network Authentication Required（需要网络认证）  |