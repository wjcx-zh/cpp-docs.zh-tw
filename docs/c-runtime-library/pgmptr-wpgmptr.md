---
title: "_pgmptr、_wpgmptr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pgmptr"
  - "_pgmptr"
  - "wpgmptr"
  - "_wpgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pgmptr 函式"
  - "_wpgmptr 函式"
  - "pgmptr 函式"
  - "wpgmptr 函式"
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pgmptr、_wpgmptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可執行檔的路徑。  取代；請使用 [\_get\_pgmptr](../c-runtime-library/reference/get-pgmptr.md) 和 [\_get\_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md)。  
  
## 語法  
  
```  
extern char *_pgmptr;  
extern wchar_t *_wpgmptr;  
```  
  
## 備註  
 當程式從命令直編譯器\(Cmd.exe\)執行時， `_pgmptr` 會自動初始化到可執行檔的完整路徑。  例如，如果 Hello.exe 在 C:\\BIN，而路徑在 C:\\BIN ，則當您執行時，`_pgmptr` 會被設為設定為 C:\\BIN\\Hello.exe  
  
```  
C> hello   
```  
  
 當程式未從命令列上執行， `_pgmptr` 可能會被初始化為程式名稱 \(不含副檔名之檔案的主檔名 \(Base Name\) 或檔案名稱、相對路徑或完整路徑。  
  
 `_wpgmptr` 是 `_pgmptr` 的寬字元副本為使用 `wmain`的程式所使用。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## 需求  
  
|變數|必要的標頭|  
|--------|-----------|  
|`_pgmptr`, `_wpgmptr`|\<stdlib.h\>|  
  
## 範例  
 以下程式將說明 `_pgmptr` 的用法。  
  
```  
// crt_pgmptr.c  
// compile with: /W3  
// The following program demonstrates the use of _pgmptr.  
//  
#include <stdio.h>  
#include <stdlib.h>  
int main( void )  
{  
   printf("The full path of the executing program is : %Fs\n",   
     _pgmptr); // C4996  
   // Note: _pgmptr is deprecated; use _get_pgmptr instead  
}  
```  
  
 您可以藉由將 `%Fs` 變更為 `%S` 和將 `main`變更為 `wmain` 以使用 `_wpgmptr` 。  
  
## 請參閱  
 [全域變數](../c-runtime-library/global-variables.md)