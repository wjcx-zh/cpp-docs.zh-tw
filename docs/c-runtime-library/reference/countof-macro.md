---
title: "_countof 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
  - "_countof"
  - "countof"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_countof 巨集"
  - "countof 巨集"
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _countof 巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算靜態配置陣列中的元素數目。  
  
## 語法  
  
```  
size_t _countof(   
   array  
);  
```  
  
#### 參數  
 `array`  
 陣列的名稱。  
  
## 傳回值  
 陣列中的元素數目，表示為 `size_t`。  
  
## 備註  
 請確定 `array` 實際上是陣列，而不是指標。  在 C 中，如果 `array` 是指標，則 `_countof` 將產生錯誤的結果。  在 C\+\+ 中，如果 `array` 是指標，則 `_countof` 將無法編譯。  
  
## 需求  
  
|巨集|必要的標頭|  
|--------|-----------|  
|`_countof`|\<stdlib.h\>|  
  
## 範例  
  
```  
// crt_countof.cpp  
#define _UNICODE  
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
  
int main( void )  
{  
   _TCHAR arr[20], *p;  
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );  
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );  
   // In C++, the following line would generate a compile-time error:  
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)  
  
   _tcscpy_s( arr, _countof(arr), _T("a string") );  
   // unlike sizeof, _countof works here for both narrow- and wide-character strings  
}  
```  
  
  **sizeof\(arr\) \= 40 個位元組**  
**\_countof\(arr\) \= 20 個元素**   
## 請參閱  
 [sizeof 運算子](../../cpp/sizeof-operator.md)