---
title: "_CrtSetDumpClient | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetDumpClient"
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
  - "_CrtSetDumpClient"
  - "CrtSetDumpClient"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient 函式"
  - "CrtSetDumpClient 函式"
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtSetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安裝應用程式定義的函式以傾印 `_CLIENT_BLOCK` 型別記憶體區塊 \(僅偵錯版本\)。  
  
## 語法  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### 參數  
 `dumpClient`  
 加入用戶端定義記憶體傾印功能到攔截執行階段 C 偵錯記憶體傾印處理序。  
  
## 傳回值  
 傳回先前定義的用戶端區塊傾印函式。  
  
## 備註  
 `_CrtSetDumpClient` 函式可讓應用程式將它的函式攔截到存於 `_CLIENT_BLOCK` 記憶體區塊的傾印物件至執行階段 C 偵錯記憶體傾印程序。  因此，每次一個偵錯傾印函式，例如 [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 或 [\_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) 傾印 `_CLIENT_BLOCK` 記憶體區塊，應用程式的傾印函式同樣如此呼叫。  `_CrtSetDumpClient` 提供應用程式以簡單方法偵測記憶體遺漏和驗證或報告在 `_CLIENT_BLOCK` 區塊存放的資料內容。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtSetDumpClient` 的呼叫將被移除。  
  
 `_CrtSetDumpClient` 函式安裝在 `dumpClient` 所指定的新應用程式端定義的傾印功能並傳回先前定義的傾印函式。  用戶端區塊傾印函式的範例如下:  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` 引數是指向使用者記憶體區塊的資料區段的開頭，而 `blockSize` 以位元組指定配置的記憶體區塊的大小。  用戶端區塊傾印函式必須傳回 `void`。  傳入 `_CrtSetDumpClient` 的指向客戶端傾印函數的指標是定義在 Crtdbg.h 裡的 `_CRT_DUMP_CLIENT` 類型：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 如需在 `_CLIENT_BLOCK` 型別的記憶體區塊上執行的函式的詳細資訊，請參閱 [用戶端區塊攔截函式](../Topic/Client%20Block%20Hook%20Functions.md)。  [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) 函式可用來傳回有關區塊類型及子類型的資訊。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtSetDumpClient`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)