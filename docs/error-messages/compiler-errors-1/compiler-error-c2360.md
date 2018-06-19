---
title: 編譯器錯誤 C2360 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2360
dev_langs:
- C++
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c24a44222a01d66c57aab340c5a06469f212e285
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196281"
---
# <a name="compiler-error-c2360"></a>編譯器錯誤 C2360
'identifier' 的初始化會被 'case' 標籤略過  
  
 初始化`identifier`中就可以略過`switch`陳述式。 除非宣告括在區塊中，您不能跳過的初始設定式宣告。 (直到結束區塊內宣告，除非變數是範圍內`switch`陳述式。)  
  
 下列範例會產生 C2360:  
  
```  
// C2360.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   case 1 :   // C2360  
      int k = 1;  
   }  
}  
```  
  
 可能的解決方式：  
  
```  
// C2360b.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   case 1 :  
      int k = 1;  
   }  
}  
```