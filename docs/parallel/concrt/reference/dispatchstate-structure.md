---
title: "DispatchState 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::DispatchState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DispatchState 結構"
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: 17
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DispatchState 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`DispatchState` 結構用來將狀態傳輸至 `IExecutionContext::Dispatch` 方法。  它描述在 `IExecutionContext` 介面上叫用 `Dispatch` 方法的情況。  
  
## 語法  
  
```  
struct DispatchState;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[DispatchState::DispatchState 建構函式](../Topic/DispatchState::DispatchState%20Constructor.md)|建構新的 `DispatchState` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[DispatchState::m\_dispatchStateSize 資料成員](../Topic/DispatchState::m_dispatchStateSize%20Data%20Member.md)|這個結構的大小，用於版本控制。|  
|[DispatchState::m\_fIsPreviousContextAsynchronouslyBlocked 資料成員](../Topic/DispatchState::m_fIsPreviousContextAsynchronouslyBlocked%20Data%20Member.md)|指示此內容是否已經因為前一個內容以非同步方式封鎖而進入 `Dispatch` 方法。  這只能用於 UMS 排程內容，而且會將其他所有執行內容設為 `0` 值。|  
|[DispatchState::m\_reserved 資料成員](../Topic/DispatchState::m_reserved%20Data%20Member.md)|保留供未來傳遞資訊的位元。|  
  
## 繼承階層架構  
 `DispatchState`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext::Dispatch 方法](../Topic/IExecutionContext::Dispatch%20Method.md)