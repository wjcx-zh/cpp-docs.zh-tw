---
title: "scheduler_worker_creation_error 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::scheduler_worker_creation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_worker_creation_error 類別"
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# scheduler_worker_creation_error 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述因為無法建立並行執行階段中的背景工作執行內容而擲回的例外狀況。  
  
## 語法  
  
```  
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[scheduler\_worker\_creation\_error::scheduler\_worker\_creation\_error 建構函式](../Topic/scheduler_worker_creation_error::scheduler_worker_creation_error%20Constructor.md)|多載。  建構 `scheduler_worker_creation_error` 物件。|  
  
## 備註  
 從並行執行階段呼叫作業系統建立執行內容失敗時，通常會擲回此例外狀況。  執行內容是執行在並行執行階段工作的執行緒。  通常會從呼叫傳回到 Win32 方法 `GetLastError` 的錯誤碼會轉換成型別 `HRESULT` 的值，並且可以使用基礎類別 `get_error_code` 方法擷取。  
  
## 繼承階層  
 `exception`  
  
 [scheduler\_resource\_allocation\_error](../../../parallel/concrt/reference/scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)