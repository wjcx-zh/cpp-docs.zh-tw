---
title: "_get_pgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_pgmptr"
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
  - "get_pgmptr"
  - "_get_pgmptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_pgmptr 函式"
  - "_pgmptr 全域變數"
  - "get_pgmptr 函式"
  - "pgmptr 全域變數"
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _get_pgmptr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得 `_pgmptr`全域變數的目前值。  
  
## 語法  
  
```  
errno_t _get_pgmptr(   
   char **pValue   
);  
```  
  
#### 參數  
 \[out\] `pValue`  
 要填入資料的指標 `_pgmptr` 變數的目前值。  
  
## 傳回值  
 如果成功則回傳零，如果失敗則為錯誤碼。  如果 `pValue` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
## 備註  
 `_pgmptr` 全域變數包含可執行檔與流程的完整路徑。  如需詳細資訊，請參閱[\_pgmptr、\_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_pgmptr`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_get\_wpgmptr](../../c-runtime-library/reference/get-wpgmptr.md)