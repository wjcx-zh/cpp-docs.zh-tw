---
title: "_CrtIsMemoryBlock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtIsMemoryBlock"
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
apitype: "DLLExport"
f1_keywords: 
  - "CrtlsMemoryBlock"
  - "_CrtIsMemoryBlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtIsMemoryBlock 函式"
  - "CrtIsMemoryBlock 函式"
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _CrtIsMemoryBlock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

確認指定的記憶體區塊在本機堆積，並有有效的偵錯堆積區塊類型識別項 \(僅偵錯版本\)。  
  
## 語法  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### 參數  
 \[in\] `userData`  
 要驗證的記憶體區塊的開頭的指標。  
  
 \[in\] `size`  
 單位為位元組的區塊大小。  
  
 \[out\] `requestNumber`  
 對區塊配置數量或 `NULL`的指標。  
  
 \[out\] `filename`  
 指向要求區塊或 `NULL` 的來源檔案名稱之指標。  
  
 \[out\] `linenumber`  
 對在原始程式檔的行號或 `NULL` 的指標。  
  
## 傳回值  
 如果指定的記憶體區塊在本機堆積內且有有效的偵錯堆積區塊類型的識別項，`_CrtIsMemoryBlock` 會傳回 `TRUE` ;否則，函式會傳回 `FALSE`。  
  
## 備註  
 `_CrtIsMemoryBlock` 函式會驗證指定的記憶體區塊在應用程式的本機堆積中，而且有有效的區塊類型的識別項。  這個函式也可以用來取得物件配置順序編號和記憶體區塊配置原始要求的原始程式檔名稱和行號。  如果在本機堆積找到區塊，傳遞 `requestNumber`的非 null 值， `filename`或 `linenumber` 參數造成 `_CrtIsMemoryBlock` 設定這些參數為記憶體區塊的偵錯標頭。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtIsMemoryBlock` 的呼叫將被移除。  
  
 如果 `_CrtIsMemoryBlock` 失敗，則傳回 `FALSE` ，並將輸出參數初始化為預設值: `requestNumber` 和 `lineNumber` 設定為 0，而 `filename` 設定為 `NULL`。  
  
 由於這個函式會傳回 `TRUE` 或 `FALSE`，它可以傳遞至其中一個 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集以建立一個簡單的偵錯錯誤處理機制。  如果指定的位址不在本機堆積中，尋找下列範例造成判斷提示失敗:  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 如需 `_CrtIsMemoryBlock` 如何與其他偵錯功能和巨集一起使用的詳細資訊，請參閱 [報告巨集](../Topic/Macros%20for%20Reporting.md)。  如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 參閱 [CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 類別主題的的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)