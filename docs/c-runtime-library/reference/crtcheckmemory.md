---
title: "_CrtCheckMemory | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtCheckMemory"
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
  - "CrtCheckMemory"
  - "_CrtCheckMemory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtCheckMemory 函式"
  - "CrtCheckMemory 函式"
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtCheckMemory
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在偵錯堆積中檢查配置的記憶體區塊的完整性 \(僅偵錯版本\)。  
  
## 語法  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## 傳回值  
 如果成功，則 `_CrtCheckMemory` 會傳回 TRUE;否則，函式會傳回 FALSE。  
  
## 備註  
 `_CrtCheckMemory` 函式是由偵錯堆積管理員就會驗證配置來驗證基礎基底堆積並檢查每個記憶體區塊。  如果錯誤或記憶體不一致在基礎基底堆積、偵錯標頭資訊或覆寫緩衝區發生， `_CrtCheckMemory` 會產生與描述錯誤條件的資訊的偵錯報告。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtCheckMemory` 的呼叫將被移除。  
  
 使用 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式， `_CrtCheckMemory` 行為可以透過設定 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的位元欄位控制項。  將 **\_CRTDBG\_CHECK\_ALWAYS\_DF** 位元欄位打開會導致 `_CrtCheckMemory` 在每一次記憶體配置被要求時呼叫。  雖然這個方法會拖慢執行，但對於快速尋找錯誤很有用。  將 **\_CRTDBG\_ALLOC\_MEM\_DF** 位元欄位關掉會導致 `_CrtCheckMemory` 不去驗證堆積且立即傳回 **TRUE**。  
  
 由於這個函式會傳回 **TRUE** 或 **FALSE**，它可以傳遞至 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集之一，以建立一個簡單的偵錯錯誤處理機制。  如果在堆積損毀，偵測到下列範例造成判斷提示失敗:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 如需 `_CrtCheckMemory` 如何運作的詳細資訊可以使用與其他偵錯功能，請參閱 [堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  如需記憶體管理和偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtCheckMemory`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 如需 `_CrtCheckMemory` 使用方式的範例，請參閱 [crt\_dbg1](http://msdn.microsoft.com/zh-tw/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## .NET Framework 對等用法  
 [System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)