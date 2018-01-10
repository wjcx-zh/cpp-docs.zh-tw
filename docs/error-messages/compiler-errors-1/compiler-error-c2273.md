---
title: "編譯器錯誤 C2273 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2273
dev_langs: C++
helpviewer_keywords: C2273
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c08e746034d066dd73d172045ce796bf4f74de0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2273"></a>編譯器錯誤 C2273
'type'：當做 '->' 運算子的右邊不合法  
  
 類型會顯示為的右運算元`->`運算子。  
  
 這個錯誤可能被因嘗試存取使用者定義型別轉換。 在 -> 與 `operator` 之間使用關鍵字 `type`。  
  
 下列範例會產生 C2273:  
  
```  
// C2273.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
int main() {  
   MyClass * ClassPtr = new MyClass;  
   int i = ClassPtr->int();   // C2273  
   int j = ClassPtr-> operator int();   // OK  
}  
```