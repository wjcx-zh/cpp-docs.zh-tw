---
title: 編譯器錯誤 C2361 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2361
dev_langs:
- C++
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9223916543119c16fc5d8c19bf5cb9ae38e77909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222276"
---
# <a name="compiler-error-c2361"></a>編譯器錯誤 C2361
'identifier' 的初始化會被 'default' 標籤略過  
  
 初始化`identifier`中就可以略過`switch`陳述式。 除非宣告括在區塊中，您不能跳過的初始設定式宣告。 (直到結束區塊內宣告，除非變數是範圍內`switch`陳述式。)  
  
 下列範例會產生 C2361:  
  
```  
// C2361.cpp  
void func( void ) {  
   int x;  
   switch (x) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   default :   // C2361 error  
      int k = 1;  
   }  
}  
```  
  
 可能的解決方式：  
  
```  
// C2361b.cpp  
// compile with: /c  
void func( void ) {  
   int x = 0;  
   switch (x) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   default :  
      int k = 1;  
   }  
}  
```