---
title: 編譯器錯誤 C2561 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8ece9a3d9347a5179844cbfca3425870c25e2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2561"></a>編譯器錯誤 C2561
'identifier': 函式必須傳回值  
  
 此函式宣告為傳回值，但未包含函式定義`return`陳述式。  
  
 這個錯誤可能被因不正確的函式原型：  
  
1.  如果函式不會傳回值，宣告函式傳回型別[void](../../cpp/void-cpp.md)。  
  
2.  檢查所有可能的分支，函式的傳回類型在原型中宣告的值。  
  
3.  包含儲存傳回值中的內嵌組件常式的 c + + 函式`AX`暫存器可能需要的 return 陳述式。 中的值複製`AX`到暫存變數，並從函式傳回該變數。  
  
 下列範例會產生 C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```