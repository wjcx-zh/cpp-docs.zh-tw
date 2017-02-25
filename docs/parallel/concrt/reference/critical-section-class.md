---
title: "critical_section 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::critical_section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "critical_section 類別"
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# critical_section 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

明確察覺並行執行階段的 Non\-reentrant Mutex。  
  
## 語法  
  
```  
class critical_section;  
```  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`native_handle_type`|`critical_section` 物件的參考。|  
  
### 公用類別  
  
|名稱|說明|  
|--------|--------|  
|[critical\_section::scoped\_lock 類別](../Topic/critical_section::scoped_lock%20Class.md)|`critical_section` 物件的例外狀況安全 RAII 包裝函式。|  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[critical\_section::critical\_section 建構函式](../Topic/critical_section::critical_section%20Constructor.md)|建構新的關鍵區段。|  
|[critical\_section::~critical\_section 解構函式](../Topic/critical_section::~critical_section%20Destructor.md)|終結關鍵區段。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[critical\_section::lock 方法](../Topic/critical_section::lock%20Method.md)|取得這個關鍵區段。|  
|[critical\_section::native\_handle 方法](../Topic/critical_section::native_handle%20Method.md)|傳回特定平台原生控制代碼 \(如果存在的話\)。|  
|[critical\_section::try\_lock 方法](../Topic/critical_section::try_lock%20Method.md)|嘗試取得鎖定，而不需封鎖。|  
|[critical\_section::try\_lock\_for 方法](../Topic/critical_section::try_lock_for%20Method.md)|嘗試取得鎖定，而不封鎖以特定數目的毫秒數。|  
|[critical\_section::unlock 方法](../Topic/critical_section::unlock%20Method.md)|解除鎖定關鍵區段。|  
  
## 備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 繼承階層  
 `critical_section`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [reader\_writer\_lock 類別](../../../parallel/concrt/reference/reader-writer-lock-class.md)