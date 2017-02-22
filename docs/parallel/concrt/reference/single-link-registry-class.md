---
title: "single_link_registry 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::single_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single_link_registry 類別"
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# single_link_registry 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`single_link_registry` 物件是只管理單一來源或目標區塊的 `network_link_registry`。  
  
## 語法  
  
```  
template<  
   class _Block  
>  
class single_link_registry : public network_link_registry<_Block>;  
```  
  
#### 參數  
 `_Block`  
 存放在 `single_link_registry` 物件的區塊資料型別。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[single\_link\_registry::single\_link\_registry 建構函式](../Topic/single_link_registry::single_link_registry%20Constructor.md)|建構 `single_link_registry` 物件。|  
|[single\_link\_registry::~single\_link\_registry 解構函式](../Topic/single_link_registry::~single_link_registry%20Destructor.md)|終結 `single_link_registry` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[single\_link\_registry::add 方法](../Topic/single_link_registry::add%20Method.md)|將連結加入至 `single_link_registry` 物件。\(會覆寫 [network\_link\_registry::add](../Topic/network_link_registry::add%20Method.md)\)。|  
|[single\_link\_registry::begin 方法](../Topic/single_link_registry::begin%20Method.md)|將 Iterator 傳回 `single_link_registry` 物件中的第一個項目。\(會覆寫 [network\_link\_registry::begin](../Topic/network_link_registry::begin%20Method.md)\)。|  
|[single\_link\_registry::contains 方法](../Topic/single_link_registry::contains%20Method.md)|在 `single_link_registry` 物件中搜尋指定的區塊。\(會覆寫 [network\_link\_registry::contains](../Topic/network_link_registry::contains%20Method.md)\)。|  
|[single\_link\_registry::count 方法](../Topic/single_link_registry::count%20Method.md)|計算 `single_link_registry` 物件中的項目數。\(會覆寫 [network\_link\_registry::count](../Topic/network_link_registry::count%20Method.md)\)。|  
|[single\_link\_registry::remove 方法](../Topic/single_link_registry::remove%20Method.md)|移除 `single_link_registry` 物件中的連結。\(會覆寫 [network\_link\_registry::remove](../Topic/network_link_registry::remove%20Method.md)\)。|  
  
## 繼承階層  
 [network\_link\_registry](../../../parallel/concrt/reference/network-link-registry-class.md)  
  
 `single_link_registry`  
  
## 需求  
 **標頭：** agents.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [multi\_link\_registry 類別](../../../parallel/concrt/reference/multi-link-registry-class.md)