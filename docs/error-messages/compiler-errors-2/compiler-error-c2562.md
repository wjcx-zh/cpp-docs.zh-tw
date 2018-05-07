---
title: 編譯器錯誤 C2562 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2562
dev_langs:
- C++
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab3fd1a5eae008785a688bcbade674425fc8b2ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2562"></a>編譯器錯誤 C2562
'identifier': 'void' 傳回值的函式  
  
 此函式宣告為`void`但傳回的值。  
  
 這個錯誤可能被因不正確的函式原型。  
  
 如果您在函式宣告中指定的傳回型別，可能會修正此錯誤。  
  
 下列範例會產生 C2562:  
  
```  
// C2562.cpp  
// compile with: /c  
void testfunc() {  
   int i;  
   return i;   // C2562 delete the return to resolve  
}  
```