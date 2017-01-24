---
title: "concurrent_priority_queue 類別 | Microsoft Docs"
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
  - "concurrent_priority_queue/concurrency::concurrent_priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_priority_queue 類別"
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_priority_queue 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_priority_queue` 類別允許多個執行緒同時推入和移除項目。  項目會以優先權順序做為移除依據，而優先權由函子提供的樣板引數決定。  
  
## 語法  
  
```  
template <  
   typename _Ty,  
   typename _Compare=std::less<_Ty>,  
   typename _Ax = std::allocator<_Ty>  
>  
, typename _Ax = std::allocator<_Ty> > class concurrent_priority_queue;  
```  
  
#### 參數  
 `_Ty`  
 要儲存在優先權佇列中的資料類型。  
  
 `_Compare`  
 可以比較兩個項目值做為排序鍵判斷其在優先權佇列中相對順序的函示物件的型別。  這個引數是選擇性的，而且二進位述詞 `less<``_Ty``>` 是預設值。  
  
 `_Ax`  
 代表預存配置器物件，此物件會封裝有關配置和解除配置並行優先權佇列之記憶體的詳細資訊的類型。  此引數是選擇性的，而且預設值是 `allocator<``_Ty``>`。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`allocator_type`|代表並行優先權佇列的配置器類別的型別。|  
|`const_reference`|表示這個型別的項目的常數參考的型別在一個同時優先權佇列儲存。|  
|`reference`|表示這個型別的項目的參考的型別在一個同時優先權佇列儲存。|  
|`size_type`|會計算並行優先權佇列中的項目數量的型別。|  
|`value_type`|代表存放在並行優先權佇列中的資料類型的型別。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[concurrent\_priority\_queue::concurrent\_priority\_queue 建構函式](../Topic/concurrent_priority_queue::concurrent_priority_queue%20Constructor.md)|多載。  建構並行優先權佇列。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[concurrent\_priority\_queue::clear 方法](../Topic/concurrent_priority_queue::clear%20Method.md)|會清除並行優先權中的所有項目。  這個方法不是並行安全的。|  
|[concurrent\_priority\_queue::empty 方法](../Topic/concurrent_priority_queue::empty%20Method.md)|測試呼叫此方法時並行優先權佇列是否是空的。  這個方法是並行安全的。|  
|[concurrent\_priority\_queue::get\_allocator 方法](../Topic/concurrent_priority_queue::get_allocator%20Method.md)|傳回用來建構並行優先權佇列配置器的複本。  這個方法是並行安全的。|  
|[concurrent\_priority\_queue::push 方法](../Topic/concurrent_priority_queue::push%20Method.md)|多載。  將項目加入至同時優先權佇列。  這個方法是並行安全的。|  
|[concurrent\_priority\_queue::size 方法](../Topic/concurrent_priority_queue::size%20Method.md)|傳回目前在並行優先權佇列中的項目數目。  這個方法是並行安全的。|  
|[concurrent\_priority\_queue::swap 方法](../Topic/concurrent_priority_queue::swap%20Method.md)|交換兩個同時優先權佇列內容。  這個方法不是並行安全的。|  
|[concurrent\_priority\_queue::try\_pop 方法](../Topic/concurrent_priority_queue::try_pop%20Method.md)|如果佇列不是空的，並傳回佇列中最高優先權的項目。  這個方法是並行安全的。|  
  
### 公用運算子  
  
|名稱|說明|  
|--------|--------|  
|[concurrent\_priority\_queue::operator\= 運算子](../Topic/concurrent_priority_queue::operator=%20Operator.md)|多載。  將另一個 `concurrent_priority_queue` 物件的內容指派給這一個。  這個方法不是並行安全的。|  
  
## 備註  
 如需關於 `concurrent_priority_queue` 類別的詳細資訊，請參閱 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 繼承階層  
 `concurrent_priority_queue`  
  
## 需求  
 **標頭：** concurrent\_priority\_queue.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)