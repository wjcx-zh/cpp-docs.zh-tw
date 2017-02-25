---
title: "scheduler_resource_allocation_error 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::scheduler_resource_allocation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_resource_allocation_error 類別"
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# scheduler_resource_allocation_error 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述因無法在並行執行階段中取得關鍵來源而擲回的例外狀況。  
  
## 語法  
  
```  
class scheduler_resource_allocation_error : public std::exception;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[scheduler\_resource\_allocation\_error::scheduler\_resource\_allocation\_error 建構函式](../Topic/scheduler_resource_allocation_error::scheduler_resource_allocation_error%20Constructor.md)|多載。  建構 `scheduler_resource_allocation_error` 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[scheduler\_resource\_allocation\_error::get\_error\_code 方法](../Topic/scheduler_resource_allocation_error::get_error_code%20Method.md)|傳回造成例外狀況的錯誤碼。|  
  
## 備註  
 從並行執行階段呼叫作業系統失敗時，通常會擲回此例外狀況。  通常會從呼叫傳回到 Win32 方法 `GetLastError` 的錯誤碼會轉換成型別 `HRESULT` 的值，並且可以使用 `get_error_code` 方法擷取。  
  
## 繼承階層  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)