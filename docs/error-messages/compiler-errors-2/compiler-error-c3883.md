---
title: 編譯器錯誤 C3883 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3883
dev_langs:
- C++
helpviewer_keywords:
- C3883
ms.assetid: cdd1c1f4-f268-4469-9c62-d52303114b0c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6841a0ab5b5f1c61159b11d2aa559863189580e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3883"></a>編譯器錯誤 C3883
'var': initonly 靜態資料成員必須初始化  
  
 變數標記為[initonly](../../dotnet/initonly-cpp-cli.md)未正確初始化。  
  
 下列範例會產生 C3883:  
  
```  
// C3883.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   static int staticConst1;   // C3883  
};  
```  
  
 下列範例示範可能的解決方式：  
  
```  
// C3883b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int staticConst2 = 0;  
};  
```  
  
 下列範例會示範如何初始化在靜態建構函式：  
  
```  
// C3883c.cpp  
// compile with: /clr /LD  
ref struct Y1 {  
   initonly  
   static int staticConst1;  
  
   static Y1() {  
      staticConst1 = 0;  
   }  
};  
```