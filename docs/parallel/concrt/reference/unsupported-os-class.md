---
title: "unsupported_os 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::unsupported_os"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_os 類別"
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# unsupported_os 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別描述使用不支援的作業系統時擲回的例外狀況。  
  
## 語法  
  
```  
class unsupported_os : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[unsupported\_os::unsupported\_os 建構函式](../Topic/unsupported_os::unsupported_os%20Constructor.md)|多載。  建構 `unsupported_os` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `unsupported_os`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)