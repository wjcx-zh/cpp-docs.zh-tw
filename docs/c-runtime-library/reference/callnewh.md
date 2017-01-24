---
title: "_callnewh | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_callnewh"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_callnewh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_callnewh"
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _callnewh
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫目前安裝的 *新處理常式*。  
  
## 語法  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
  
```  
  
#### 參數  
 `size`  
 [new 運算子](../../cpp/new-operator-cpp.md) 嘗試配置的記憶體空間。  
  
## 傳回值  
  
|值|描述|  
|-------|--------|  
|0|失敗：未安裝新處理常式或沒有任何新處理常式正在使用中。|  
|1|成功：新處理常式已安裝且作用中。  記憶體配置可以不斷重試。|  
  
## 例外狀況  
 如果找不到 *新處理常式*，此函式會擲回 [bad\_alloc](../../standard-library/bad-alloc-class.md) 。  
  
## 備註  
 如果 [new 運算子](../../cpp/new-operator-cpp.md) 無法成功配置記憶體，則會呼叫 *新處理常式*。  新處理常式可能會嘗試做一些修正的動作，例如釋放記憶體，以便讓後續的配置成功。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_callnewh|internal.h|  
  
## 請參閱  
 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md)   
 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md)