分成 User, Business, Server 三個區塊(或是稱作 Application, Core, Infrastructure) 。

User 相依 Business, Server 相依 Business

在自動化測試階段，可以分別做到 Business 獨立測試， User-Business or Business-Server 的整合測試。


Business 驅動 Server-Side, 但我們將透過 Port/ Adapter 來反向注入，使 Server-Side 相依 Business 。