---
title: "source_link_manager 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::source_link_manager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_link_manager 類別"
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# source_link_manager 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`source_link_manager` 物件會管理 `ISource` 區塊與傳訊區塊網路的連結。  
  
## 語法  
  
```  
template<  
   class _LinkRegistry  
>  
class source_link_manager;  
```  
  
#### 參數  
 `_LinkRegistry`  
 網路連結登錄。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`const_pointer`|針對 `source_link_manager` 物件中的 `const` 項目提供指標的類型。|  
|`const_reference`|型別，針對存放在並行佇列中的 `source_link_manager` 物件提供參考，以讀取及執行 `const`作業。|  
|`iterator`|型別，提供隨機存取 Iterator，可以讀取或修改 `source_link_manager` 物件中的任何項目。|  
|`type`|連結登錄的類型由 `source_link_manager` 物件管理。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[source\_link\_manager::source\_link\_manager 建構函式](../Topic/source_link_manager::source_link_manager%20Constructor.md)|建構 `source_link_manager` 物件。|  
|[source\_link\_manager::~source\_link\_manager 解構函式](../Topic/source_link_manager::~source_link_manager%20Destructor.md)|終結 `source_link_manager` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[source\_link\_manager::add 方法](../Topic/source_link_manager::add%20Method.md)|將來源連結加入至 `source_link_manager` 物件。|  
|[source\_link\_manager::begin 方法](../Topic/source_link_manager::begin%20Method.md)|將 Iterator 傳回 `source_link_manager` 物件中的第一個項目。|  
|[source\_link\_manager::contains 方法](../Topic/source_link_manager::contains%20Method.md)|在 `source_link_manager` 物件內的 `network_link_registry` 中搜尋指定的區塊。|  
|[source\_link\_manager::count 方法](../Topic/source_link_manager::count%20Method.md)|計算 `source_link_manager` 物件中的連結區塊數目。|  
|[source\_link\_manager::reference 方法](../Topic/source_link_manager::reference%20Method.md)|取得 `source_link_manager` 物件的參考。|  
|[source\_link\_manager::register\_target\_block 方法](../Topic/source_link_manager::register_target_block%20Method.md)|註冊保留此 `source_link_manager` 物件的目標區塊。|  
|[source\_link\_manager::release 方法](../Topic/source_link_manager::release%20Method.md)|釋放 `source_link_manager` 物件的參考。|  
|[source\_link\_manager::remove 方法](../Topic/source_link_manager::remove%20Method.md)|移除 `source_link_manager` 物件中的連結。|  
|[source\_link\_manager::set\_bound 方法](../Topic/source_link_manager::set_bound%20Method.md)|針對可以加入至這個 `source_link_manager` 物件的來源連結數目設定最大上限。|  
  
## 備註  
 目前，來源區塊是計算的參考。  這是 `network_link_registry` 物件的包裝程式，可允許並行存取連結並透過回呼參考連結。  訊息區塊 \(`target_block`s 或 `propagator_block` s'\) 應該使用這個類別做為其來源連結。  
  
## 繼承階層架構  
 `source_link_manager`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry 類別](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry 類別](../../../parallel/concrt/reference/multi-link-registry-class.md)