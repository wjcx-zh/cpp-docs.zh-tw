---
title: "_get_wpgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_wpgmptr"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_wpgmptr"
  - "_get_wpgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_wpgmptr 函式"
  - "_wpgmptr 全域變數"
  - "get_wpgmptr 函式"
  - "wpgmptr 全域變數"
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_wpgmptr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得 `_wpgmptr` 全域變數的目前值。  
  
## 語法  
  
```  
errno_t _get_wpgmptr(     wchar_t **pValue  );  
```  
  
#### 參數  
 \[輸出\] `pValue`  
 要以 `_wpgmptr` 變數的目前值填滿的字串指標。  
  
## 傳回值  
 如果成功，傳回零；如果失敗，則傳回錯誤碼。  若 `pValue` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## 備註  
 `_wpgmptr` 全域變數包含與處理相關聯的可執行檔的完整路徑做為寬字元字串。  如需詳細資訊，請參閱[\_pgmptr、\_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_wpgmptr`|\<stdlib.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_get\_pgmptr](../../c-runtime-library/reference/get-pgmptr.md)