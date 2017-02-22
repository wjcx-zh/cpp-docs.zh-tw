---
title: "invalid_compute_domain 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::invalid_compute_domain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_compute_domain 類別"
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# invalid_compute_domain 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

執行階段無法由 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 呼叫位置指定的計算區域啟動核心所擲回的的例外狀況。  
  
## 語法  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_compute\_domain::invalid\_compute\_domain 建構函式](../Topic/invalid_compute_domain::invalid_compute_domain%20Constructor.md)|初始化 `invalid_compute_domain` 類別的新執行個體。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## 需求  
 **標頭:**  amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)