---
title: "_CrtSetAllocHook | Microsoft Docs"
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
  - "_CrtSetAllocHook"
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
  - "_CrtSetAllocHook"
  - "CrtSetAllocHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtSetAllocHook 函式"
  - "CrtSetAllocHook 函式"
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetAllocHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以安裝一個客戶設置函示藉由將它安裝在 C 執行時間偵錯記憶體配置階段 \(僅偵錯版本\) 上。  
  
## 語法  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### 參數  
 `allocHook`  
 加入用戶端定義配置功能到攔截執行階段 C 偵錯記憶體配置處理序。  
  
## 傳回值  
 如果 `allocHook` 是 `NULL`，則會傳回先前定義的配置攔截函式則為 `NULL` 。  
  
## 備註  
 `_CrtSetAllocHook` 可讓應用程式掛載它的配置功能的執行階段 C 偵錯程式庫記憶體配置處理序。  因此，對一個偵錯配置功能的每個呼叫設定，重新配置或釋放記憶體區塊觸發程序呼叫應用程式的攔截函式。  `_CrtSetAllocHook` 提供應用程式以簡單方法來測試應用程式如何處理記憶體不足情況、能力檢查配置模式和機會記錄稍後分析的配置資訊。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtSetAllocHook` 的呼叫將被移除。  
  
 `_CrtSetAllocHook` 函式安裝在 `allocHook` 所指定的新用戶端定義的配置功能並傳回先前定義的攔截函式。  下列範例示範一個用戶端定義的配置攔截應該如何變為原型:  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 `allocType` 引數指定配置作業 `(_HOOK_ALLOC`、觸發呼叫配置攔截函式的 `_HOOK_REALLOC`和 `_HOOK_FREE`\)。  當觸發的配置類型為 `_HOOK_FREE`時， `userData` 指標指向要釋放的記憶體區塊的使用者資料部分。  不過，當觸發的配置類型是 `_HOOK_ALLOC` 或 `_HOOK_REALLOC`時，因為不會配置記憶體區塊， `userData` 是 `NULL` 。  
  
 `size` 以位元組指定記憶體區塊的大小， `blockType` 表示記憶體區塊類型， `requestNumber` 是記憶體區塊的物件配置的符號，因此，如果有空間的話， `filename` 和 `lineNumber` 指定啟始觸發的部署作業的原始程式檔名稱和行號。  
  
 在攔截函式處理完成後，必須傳回布林值，指示主要 C 執行階段配置處理序如何繼續。  當攔截函式要主要配置處理序繼續執行時，就好像從未攔截函式呼叫，然後攔截函式應該傳回 `TRUE`。  這會導致原始觸發的配置作業執行。  使用這個實作，攔截函式可收集和儲存稍後分析的配置資訊，卻不影響以偵錯堆積的目前配置作業或狀態。  
  
 當攔截函式需要如同觸發的配置作業呼叫和時失敗主要配置處理序以繼續時，攔截函式應該傳回 `FALSE`。  使用這個實作，攔截函式可模擬各種記憶體條件和偵錯堆積狀態測試應用程式如何處理每個條件。  
  
 若要清除攔截函式，請將 `NULL` 設定為 `_CrtSetAllocHook`。  
  
 如需 `_CrtSetAllocHook` 如何搭配其他記憶體管理函式或如何撰寫自己的用戶端定義的攔截函式的詳細資訊，請參閱 [撰寫偵錯攔截函式](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
> [!NOTE]
>  `_CrtSetAllocHook` \(不支援 IA64\) `/clr:pure`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtSetAllocHook`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 如需範例 `_CrtSetAllocHook`使用方式，請參閱 [crt\_dbg2](http://msdn.microsoft.com/zh-tw/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)