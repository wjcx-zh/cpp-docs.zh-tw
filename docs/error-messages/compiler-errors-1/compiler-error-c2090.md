---
title: 編譯器錯誤 C2090 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2090
dev_langs:
- C++
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718ed5ba8d422c2657dc58591ce285b0d85857cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2090"></a>編譯器錯誤 C2090
函式會傳回陣列  
  
 函式無法傳回陣列。 而是傳回陣列的指標。  
  
 下列範例會產生 C2090:  
  
```  
// C2090.cpp  
int func1(void)[] {}   // C2090  
```  
  
 可能的解決方式：  
  
```  
// C2090b.cpp  
// compile with: /c  
int* func2(int * i) {  
   return i;  
}  
```