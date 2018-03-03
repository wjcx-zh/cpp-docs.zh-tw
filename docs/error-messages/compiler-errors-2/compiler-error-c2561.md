---
title: "編譯器錯誤 C2561 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 604c5b4ce8c8e1b5477d076a061fdf56fdfd9c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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