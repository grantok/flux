```mermaid
---
title: Bazarr
---
graph LR
 User:::usr -- bazarr.monstersarereal.net --> ic-nginx
 client([client])-. Ingress-managed <br> nginx .->ingress[Ingress];
 ingress-->|routing rule|service[Service];
 subgraph cluster
 ingress;
 service-->pod1[Pod];
 end
 subgraph nginx
 subgraph ic-nginx [ingress-controller-nginx]
  end
 end

 subgraph f
  direction TB
  a(nginx - ingressClass)
  b[[ingress-nginx-controller - Service/Loadbalancer, externalIP, ClusterIP, pod]]
  c[/ingress-nginx-controller replicaSet/]
  a:::volume --> b --> c
 end
 classDef plain fill:#ddd,stroke:#fff,stroke-width:4px,color:#000;
 classDef k8s fill:#326ce5,stroke:#fff,stroke-width:4px,color:#fff;
 classDef cluster fill:#fff,stroke:#bbb,stroke-width:2px,color:#326ce5;
 classDef exposedPort fill:gold,stroke:black,stroke-width:2px,color:black;
 classDef volume fill:cornflowerblue,stroke:cornflowerblue,color:white;
 classDef usr fill:slategray,stroke:slategray,color:white;
 classDef ctrl fill:lightsteelblue,stroke:lightsteelblue,color:black
 classDef ingressCtrl fill:steelblue,stroke:steelblue,color:white
 class ingress,service,pod1,pod2 k8s;
 class client plain;
 class Port exposedPort;
 class Volume volume;
 class cluster cluster;
 class z volume;
 class nginx ingressCtrl
 class ic-nginx ctrl
 ```
