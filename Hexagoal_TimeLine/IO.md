input(driving): 驅動 domain
output(driven): 被 domain 反向驅動


### 命名方式
Inbound 方向的 Interface 稱作 UserCase, 
其 Adapter 稱作 Service

Outbound 方向的 Interface 稱作 Repository 或是 Port ，
如果要單一介面就選 Port ,  如果繼承 SpringData JPA 裡頭的  Repository 就稱 Repository ，其 Adapter 就稱作 Adapter


### 流程舉例<新增一位醫生流程>

controller 接收請求，調用 inbound/UserCase 去處理創建 Doctor 的動作，
其中 UserCase 會調用 Repository 去 persist Doctor 。

running the above process of create a doctor, u need the following classes and interfaces, and their implements 
>
application/DoctorController
application/service/DoctorService
application/request/CreaterDoctorRequest
application/response/CreateDoctorResponse
domain/model/Doctor
domain/inbound/CreateDoctorUserCase
domain/outbound/DoctorRepository


