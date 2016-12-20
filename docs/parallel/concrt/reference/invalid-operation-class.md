---
title: "invalid_operation 類別 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_operation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_operation 類別"
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_operation 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述例外狀況擲回執行無效的作業時，更精確地不是由另一個並行執行階段擲回的例外狀況型別描述。  
  
## 語法  
  
```  
class invalid_operation : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[invalid\_operation::invalid\_operation 建構函式](../Topic/invalid_operation::invalid_operation%20Constructor.md)|多載。  建構 `invalid_operation` 物件。|  
  
## 備註  
 會擲回這個例外狀況的各種方法通常會記錄它們擲回此例外狀況的情形。  
  
## 繼承階層架構  
 `exception`  
  
 `invalid_operation`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)