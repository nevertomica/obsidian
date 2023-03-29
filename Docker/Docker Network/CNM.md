CNM := container network modle
[[Network]]



three major building blocks
- Sandboxes：isolated network stack
- Endpoints: virtual Ethernet interface
- Networks：Virtual switch

Ethernet interfaces, ports, routing tables, DNS config

電腦要能連接網路從內到外是，
網路介面卡/ Ehterner interface → swich → router

Libnetwork 
Libnet also implements native service discovery, ingress-based container load balancing, and the network control plane and management plane functionality.

Libnetwork Doc
https://github.com/moby/libnetwork/blob/master/docs/design.md

Docker 容器實戰10
https://blog.51cto.com/u_14065119/5399494