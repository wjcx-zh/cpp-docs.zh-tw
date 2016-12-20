---
title: "_findclose | Microsoft Docs"
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
  - "_findclose"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_findclose"
  - "findclose"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_findclose 函式"
  - "findclose 函式"
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findclose
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關閉指定的搜尋控制代碼並釋放相關聯的資源。  
  
## 語法  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### 參數  
 `handle`  
 搜尋上一個呼叫傳回的 `_findfirst`的控制代碼。  
  
## 傳回值  
 如果成功，`_findclose` 會傳回 0。  否則，它會傳回– 1 並將 `errno` 設定為 `ENOENT`，表示找不到任何相符的檔案。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_findclose`|\<io.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [系統呼叫](../../c-runtime-library/system-calls.md)   
 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)