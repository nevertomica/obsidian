目的
將六角形範例搬移完成

下一步
確定可以增刪改查

截止日期
4月7日 週五

- 架構分成三層: 從左至右, Application(User-Side), Core(Business-Logic-Side), InfraStructure(Server-Side)
- Other Layers depend on Core-Layer
- Core contains ports which are the the interface used to act with other layers
- Adaptors are implements of ports 
- Adaptors of Application must be obey Interface segregation principle, and could not
  be accessed to Core's all methods
- Adaptors of Infrastructure make IoC 

主要文章
https://blog.octo.com/en/hexagonal-architecture-three-principles-and-an-implementation-example/



[[Architecture]]