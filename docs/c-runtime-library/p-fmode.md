---
title: "__p__fmode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__p__fmode"
apilocation: 
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__p__fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__p__fmode"
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __p__fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_fmode` 全域變數的指標，為檔案 I\/O 作業中指定預設的 *檔案轉譯模式* 。  
  
## 語法  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## 傳回值  
 `_fmode` 全域變數的指標。  
  
## 備註  
 `__p__fmode` 函式僅供內部使用，不應該從使用者程式碼呼叫。  
  
 檔案轉譯模式為 [\_open](../c-runtime-library/reference/open-wopen.md) 和 [\_pipe](../c-runtime-library/reference/pipe.md) I\/O 作業指定 `binary` 或 `text` 轉譯。  如需詳細資訊，請參閱[\_fmode](../c-runtime-library/fmode.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_p\_\_fmode|stdlib.h|