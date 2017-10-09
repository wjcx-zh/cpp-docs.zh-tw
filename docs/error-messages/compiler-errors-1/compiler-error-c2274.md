---
title: "編譯器錯誤 C2274 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4315d1cfef9a0583b1f44c8caa264378e32f1a35
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2274"></a>編譯器錯誤 C2274
'type': 當做的右邊不合法 '。 ' 運算子  
  
 類型會顯示為成員存取 （.） 運算子的右運算元。  
  
 這個錯誤可能被因嘗試存取使用者定義型別轉換。 使用關鍵字`operator`之間的週期和`type`。  
  
 下列範例會產生 C2286：  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```
