---
title: "scoped_d3d_access_lock 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scoped_d3d_access_lock 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

accelerator\_view 物件上的 D3D 存取鎖定的 RAII 包裝函式。  
  
## 語法  
  
```  
class scoped_d3d_access_lock;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock::scoped\_d3d\_access\_lock 建構函式](../Topic/scoped_d3d_access_lock::scoped_d3d_access_lock%20Constructor.md)|多載。  建構 `scoped_d3d_access_lock` 物件。  當這個物件超出範圍時，釋放鎖定。|  
|[scoped\_d3d\_access\_lock::~scoped\_d3d\_access\_lock 解構函式](../Topic/scoped_d3d_access_lock::~scoped_d3d_access_lock%20Destructor.md)|釋放相關聯 `accelerator_view` 物件上的 D3D 存取鎖定。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock::operator\= 運算子](../Topic/scoped_d3d_access_lock::operator=%20Operator.md)|取得其他 `scoped_d3d_access_lock` 的鎖定擁有權。|  
  
## 繼承階層架構  
 `scoped_d3d_access_lock`  
  
## 需求  
 **標頭：**amprt.h  
  
 **命名空間：**concurrency::direct3d  
  
## 請參閱  
 [Concurrency::direct3d 命名空間](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)