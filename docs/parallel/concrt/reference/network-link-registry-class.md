---
title: "network_link_registry 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::network_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "network_link_registry 類別"
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# network_link_registry 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`network_link_registry` 抽象基底類別會管理來源和目標區塊之間的連結。  
  
## 語法  
  
```  
template<  
   class _Block  
>  
class network_link_registry;  
```  
  
#### 參數  
 `_Block`  
 存放在 `network_link_registry` 中的區塊資料型別。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`const_pointer`|針對 `network_link_registry` 物件中的 `const` 項目提供指標的類型。|  
|`const_reference`|型別，針對存放在並行佇列中的 `network_link_registry` 物件提供參考，以讀取及執行 `const`作業。|  
|`iterator`|型別，提供隨機存取 Iterator，可以讀取或修改 `network_link_registry` 物件中的任何項目。|  
|`type`|型別，代表存放在 `network_link_registry` 物件中的區塊型別。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[network\_link\_registry::add 方法](../Topic/network_link_registry::add%20Method.md)|在衍生類別中覆寫時，將連結加入至 `network_link_registry` 物件。|  
|[network\_link\_registry::begin 方法](../Topic/network_link_registry::begin%20Method.md)|在衍生類別中被覆寫時，將 Iterator 傳回到 `network_link_registry` 物件中的第一個項目。|  
|[network\_link\_registry::contains 方法](../Topic/network_link_registry::contains%20Method.md)|在衍生類別中被覆寫時，搜尋指定區塊之 `network_link_registry` 物件。|  
|[network\_link\_registry::count 方法](../Topic/network_link_registry::count%20Method.md)|在衍生類別中被覆寫時，傳回 `network_link_registry` 物件中的項目數目。|  
|[network\_link\_registry::remove 方法](../Topic/network_link_registry::remove%20Method.md)|在衍生類別中覆寫時，會從 `network_link_registry` 物件移除指定的區塊。|  
  
## 備註  
 `network link registry` 不是安全的並行存取。  
  
## 繼承階層架構  
 `network_link_registry`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry 類別](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry 類別](../../../parallel/concrt/reference/multi-link-registry-class.md)