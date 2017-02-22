---
title: "concurrent_queue 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_queue/concurrency::concurrent_queue"
  - "concurrent_queue/Concurrency::concurrent_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_queue 類別"
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# concurrent_queue 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_queue` 類別序列容器類別，允許以先進先出的方式存取其項目。  它可以讓一組有限的並行存取之作業，例如`push`和`try_pop`。  
  
## 語法  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;  
```  
  
#### 參數  
 `_Ty`  
 要儲存在佇列中的資料類型。  
  
 `_Ax`  
 代表預存配置器物件 \(此物件會封裝有關配置和解除配置此並行佇列之記憶體的詳細資訊\) 的型別。  此引數是選擇性的，而且預設值是 `allocator<``_Ty``>`。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`allocator_type`|型別，代表並行佇列的配置器類別。|  
|`const_iterator`|型別，代表並行佇列中不具執行緒安全的 `const` Iterator 項目。|  
|`const_reference`|型別，針對存放在並行佇列中的 `const` 項目提供參考，以讀取及執行 `const` 作業。|  
|`difference_type`|型別，針對並行佇列中兩個項目之間提供帶正負號的距離。|  
|`iterator`|型別，代表並行佇列中不具執行緒安全的 Iterator 項目。|  
|`reference`|型別，針對存放在並行佇列中的項目提供參考。|  
|`size_type`|型別，會計算並行的佇列中的項目數量。|  
|`value_type`|型別，代表存放在並行佇列中的資料類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_queue::concurrent\_queue 建構函式](../Topic/concurrent_queue::concurrent_queue%20Constructor.md)|多載。  建構並行的佇列。|  
|[concurrent\_queue::~concurrent\_queue 解構函式](../Topic/concurrent_queue::~concurrent_queue%20Destructor.md)|終結並行的佇列。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_queue::clear 方法](../Topic/concurrent_queue::clear%20Method.md)|清除並行佇列並終結目前佇列的項目。  這個方法不是並行安全的。|  
|[concurrent\_queue::empty 方法](../Topic/concurrent_queue::empty%20Method.md)|測試呼叫此方法時並行佇列是否是空的。  這個方法是並行安全的。|  
|[concurrent\_queue::get\_allocator 方法](../Topic/concurrent_queue::get_allocator%20Method.md)|傳回用來建構並行佇列配置器的複本。  這個方法是並行安全的。|  
|[concurrent\_queue::push 方法](../Topic/concurrent_queue::push%20Method.md)|多載。  將項目加入並行佇列的尾端結尾處。  這個方法是並行安全的。|  
|[concurrent\_queue::try\_pop 方法](../Topic/concurrent_queue::try_pop%20Method.md)|如果有的話，請清除佇列中的項目。  這個方法是並行安全的。|  
|[concurrent\_queue::unsafe\_begin 方法](../Topic/concurrent_queue::unsafe_begin%20Method.md)|多載。  將 `iterator` 或 `const_iterator` 型別的 Iterator 傳回並行佇列的開頭。  這個方法不是並行安全的。|  
|[concurrent\_queue::unsafe\_end 方法](../Topic/concurrent_queue::unsafe_end%20Method.md)|多載。  將 `iterator` 或 `const_iterator`型別的 Iterator 傳回並行佇列的結尾。  這個方法不是並行安全的。|  
|[concurrent\_queue::unsafe\_size 方法](../Topic/concurrent_queue::unsafe_size%20Method.md)|傳回佇列中的項目數目。  這個方法不是並行安全的。|  
  
## 備註  
 如需詳細資訊，請參閱 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 繼承階層架構  
 `concurrent_queue`  
  
## 需求  
 **標頭：** concurrent\_queue.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)