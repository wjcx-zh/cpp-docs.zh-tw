---
title: "_set_new_mode | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_new_mode"
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
  - "set_new_mode"
  - "_set_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_new_mode 函式"
  - "處理常式模式"
  - "set_new_mode 函式"
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Sets a new handler mode for `malloc`.  
  
## 語法  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### 參數  
 `newhandlermode`  
 New handler mode for `malloc`; valid value is 0 or 1.  
  
## 傳回值  
 Returns the previous handler mode set for `malloc`.  傳回值 1 表示配置記憶體時發生錯誤， `malloc` 先前呼叫新處理常式；傳回值 0 表示成功。  如果 `newhandlermode` 引數不等於 0 或 1，則是– 1。  
  
## 備註  
 C\+\+ `_set_new_mode` 函式會將 [malloc](../../c-runtime-library/reference/malloc.md)的新處理常式模式。  新的處理常式模式表示，失敗時，`malloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `malloc` 無法配置記憶體時，`malloc` 會以 `new` 運算子因相同原因失敗時所執行的相同方式，呼叫新處理常式。  如需詳細資訊，請參閱 *C\+\+ 語言參考* 中的 [建立](../../cpp/new-operator-cpp.md) 和 [刪除](../../cpp/delete-operator-cpp.md)作業。  若要覆寫預設值，請呼叫：  
  
```  
_set_new_mode(1)  
```  
  
 及早在您的程式中呼叫，或與 Newmode.obj 連結 \(請參閱[連結選項](../../c-runtime-library/link-options.md)\)。  
  
 這個函式會驗證其參數。  如果 `newhandlermode` 是任何除了 0 或 1 以外的值，則函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，**\_**`set_new_mode`會傳回\-1，並將 `errno` 設定為 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_new_mode`|\<new.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [\_query\_new\_mode](../../c-runtime-library/reference/query-new-mode.md)