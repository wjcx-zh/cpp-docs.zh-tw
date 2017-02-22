---
title: "reader_writer_lock 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::reader_writer_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reader_writer_lock 類別"
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# reader_writer_lock 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

以寫入器偏好設定佇列為基礎且只能本機微調的讀取器\-寫入器鎖定。  鎖定授與先進先出 \(FIFO\) 存取至寫入器，並且會在連續載入寫入器的情況下影響讀取器。  
  
## 語法  
  
```  
class reader_writer_lock;  
```  
  
## Members  
  
### 公用類別  
  
|名稱|描述|  
|--------|--------|  
|[reader\_writer\_lock::scoped\_lock 類別](../Topic/reader_writer_lock::scoped_lock%20Class.md)|可用於取得 `reader_writer_lock` 鎖定物件寫入器的例外狀況安全 RAII 包裝函式。|  
|[reader\_writer\_lock::scoped\_lock\_read 類別](../Topic/reader_writer_lock::scoped_lock_read%20Class.md)|可用於取得 `reader_writer_lock` 鎖定物件讀取器的例外狀況安全 RAII 包裝函式。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[reader\_writer\_lock::reader\_writer\_lock 建構函式](../Topic/reader_writer_lock::reader_writer_lock%20Constructor.md)|建構新的 `reader_writer_lock` 物件。|  
|[reader\_writer\_lock::~reader\_writer\_lock 解構函式](../Topic/reader_writer_lock::~reader_writer_lock%20Destructor.md)|終結 `reader_writer_lock` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[reader\_writer\_lock::lock 方法](../Topic/reader_writer_lock::lock%20Method.md)|取得寫入器的讀取器\-寫入器鎖定。|  
|[reader\_writer\_lock::lock\_read 方法](../Topic/reader_writer_lock::lock_read%20Method.md)|取得讀取器的讀取器\-寫入器鎖定。  如果有寫入器，現用讀取器必須等候寫入器完成。  讀取器只會註冊鎖定，並等待寫入器釋放它。|  
|[reader\_writer\_lock::try\_lock 方法](../Topic/reader_writer_lock::try_lock%20Method.md)|嘗試取得讀取器\-寫入器鎖定寫入器而不封鎖。|  
|[reader\_writer\_lock::try\_lock\_read 方法](../Topic/reader_writer_lock::try_lock_read%20Method.md)|嘗試取得讀取器\-寫入器鎖定讀取器而不封鎖。|  
|[reader\_writer\_lock::unlock 方法](../Topic/reader_writer_lock::unlock%20Method.md)|根據鎖定者 \(讀取器或寫入器\) 來解除鎖定讀取器\-寫入器鎖定。|  
  
## 備註  
 如需詳細資訊，請參閱 [同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 繼承階層架構  
 `reader_writer_lock`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section 類別](../../../parallel/concrt/reference/critical-section-class.md)