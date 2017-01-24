---
title: "thread 類別 | Microsoft Docs"
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
  - "thread/std::thread"
dev_langs: 
  - "C++"
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# thread 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義在應用程式中用來檢視和管理執行緒的物件。  
  
## 語法  
  
```  
class thread;  
```  
  
## 備註  
 您可以使用 `thread` 在應用程式中檢視和管理執行緒的物件。  使用預設建構函式\(與任何正在執行的執行緒無關\)建立的執行緒物件。  使用可呼叫的物件建構的執行緒物件，會建立新的執行的執行緒，並在其中呼叫可呼叫的物件。  執行緒物件可以移動，但不能複製。  因此，執行的執行緒只能與一個執行緒物件有關聯。  
  
 每個執行的執行緒都有獨特的識別碼型別 `thread::id`。  `this_thread::get_id` 函式會傳回呼叫執行緒的識別項。  函式成員 `thread::get_id` 會傳回由執行緒物件管理的執行緒的識別項。  對於預設建構的執行緒物件， `thread::get_id` 的方法會傳回跟預設建構的執行緒物件一樣的物件，而與從 `this_thread::get_id` 傳回的物件不同，其對於任何執行的執行緒可在呼叫時被加入。  
  
## 成員  
  
### 公用類別  
  
|Name|說明|  
|----------|--------|  
|[thread::id 類別](../Topic/thread::id%20Class.md)|獨特的識別有關聯的執行緒。|  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[thread::thread 建構函式](../Topic/thread::thread%20Constructor.md)|建構 `thread` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[thread::detach 方法](../Topic/thread::detach%20Method.md)|中斷與 `thread` 物件有所關聯的執行緒。|  
|[thread::get\_id 方法](../Topic/thread::get_id%20Method.md)|傳回相關執行緒的唯一識別項。|  
|[thread::hardware\_concurrency 方法](../Topic/thread::hardware_concurrency%20Method.md)|靜態。  傳回硬體執行緒內容數目的估計值。|  
|[thread::join 方法](../Topic/thread::join%20Method.md)|攔阻直到關聯的執行緒完成。|  
|[thread::joinable 方法](../Topic/thread::joinable%20Method.md)|指定相關執行緒是否可連結。|  
|[thread::native\_handle 方法](../Topic/thread::native_handle%20Method.md)|傳回表示執行緒控制代碼的實作特定的型別。|  
|[thread::swap 方法](../Topic/thread::swap%20Method.md)|使用指定 `thread` 的物件交換物件狀態。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[thread::operator\= 運算子](../Topic/thread::operator=%20Operator.md)|使執行緒和目前的 `thread` 物件有所關聯。|  
  
## 需求  
 **標題:** thread  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread\>](../standard-library/thread.md)