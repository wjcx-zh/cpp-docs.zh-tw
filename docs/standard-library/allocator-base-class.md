---
title: "allocator_base 類別 | Microsoft Docs"
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
  - "allocators.allocator_base"
  - "stdext.allocators.allocator_base"
  - "allocator_base"
  - "allocators/stdext::allocator_base"
  - "stdext::allocator_base"
  - "stdext::allocators::allocator_base"
  - "allocators/stdext::allocators::allocator_base"
  - "allocators::allocator_base"
  - "stdext.allocator_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_base 類別"
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義從同步處理篩選條件建立使用者定義的配置器時所需的基底類別和一般功能。  
  
## 語法  
  
```  
template <class Type, class Sync> class allocator_base  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Type`|配置器所配置的元素類型。|  
|`Sync`|配置器的同步處理原則，即 [sync\_none 類別](../standard-library/sync-none-class.md)、[sync\_per\_container 類別](../standard-library/sync-per-container-class.md)、[sync\_per\_thread 類別](../standard-library/sync-per-thread-class.md) 或 [sync\_shared 類別](../standard-library/sync-shared-class.md)。|  
  
### 建構函式  
  
|||  
|-|-|  
|[allocator\_base](../Topic/allocator_base::allocator_base.md)|建構類型 `allocator_base` 的物件。|  
  
### TypeDefs  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator_base::const_pointer.md)|一種類型，可提供配置器管理之物件類型的常數指標。|  
|[const\_reference](../Topic/allocator_base::const_reference.md)|一種類型，可提供配置器管理之物件類型的常數參考。|  
|[difference\_type](../Topic/allocator_base::difference_type.md)|帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。|  
|[指標](../Topic/allocator_base::pointer.md)|一種類型，可提供配置器管理之物件類型的指標。|  
|[參考](../Topic/allocator_base::reference.md)|一種類型，可提供配置器管理之物件類型的參考。|  
|[size\_type](../Topic/allocator_base::size_type.md)|不帶正負號的整數類型，可以代表樣板類別 `allocator_base` 的物件可配置的任何序列的長度。|  
|[value\_type](../Topic/allocator_base::value_type.md)|配置器所管理的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[\_Charalloc](../Topic/allocator_base::_Charalloc.md)|為類型 `char` 的陣列配置儲存體。|  
|[\_Chardealloc](../Topic/allocator_base::_Chardealloc.md)|為包含類型 `char` 之元素的陣列釋放儲存體。|  
|[位址](../Topic/allocator_base::address.md)|尋找指定值所屬物件的位址。|  
|[allocate](../Topic/allocator_base::allocate.md)|配置夠大的記憶體區塊，至少儲存某些指定的項目數。|  
|[建構](../Topic/allocator_base::construct.md)|在指定值初始化的指定位址上，建構特定類型的物件。|  
|[取消配置](../Topic/allocator_base::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[終結](../Topic/allocator_base::destroy.md)|呼叫物件解構函式，而不取消配置儲存物件的記憶體。|  
|[max\_size](../Topic/allocator_base::max_size.md)|傳回在可用記憶體用完之前，無法由類別配置器的物件配置之類型 `Type` 的元素數。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)