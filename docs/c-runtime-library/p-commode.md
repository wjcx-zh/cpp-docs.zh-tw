---
title: "__p__commode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__p__commode"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__commode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__commode"
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# __p__commode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_commode` 全域變數的指標，為檔案 I\/O 作業中指定預設的 *檔案提交模式* 。  
  
## 語法  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## 傳回值  
 `_commode` 全域變數的指標。  
  
## 備註  
 `__p__commode` 函式僅供內部使用，不應該從使用者程式碼呼叫。  
  
 檔案認可模式指定重要資料時寫入磁碟。  如需詳細資訊，請參閱[fflush](../c-runtime-library/reference/fflush.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_p\_\_commode|internal.h|