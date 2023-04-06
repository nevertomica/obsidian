目的: 了解核心是什麼,  如何用核心分出架構
下一步: 將 create 重新解讀，並將更新這一動作嘗試進行分層。

六角形架構分成下面四層：
core, application, infrastructure, common(不知道分類的)

core: business, validations, ports
application: provide to end user and what they interfact with 
infrastructure: db

商業邏輯都放在 domain, 並開出對內對外的所有接口,  接口的實踐都在上下層內。

[Netflix 六角形架構](https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749)

[[NR]]