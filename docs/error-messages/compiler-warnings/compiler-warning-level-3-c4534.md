---
title: 編譯器警告 （層級 3） C4534 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c4534
dev_langs:
- C++
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b765f5f654c8d533b0ae22d874e7657cd10d667
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4534"></a>編譯器警告 (層級 3) C4534
'constructor' 將不會類別 'class'，因為預設的引數的預設建構函式  
  
 Unmanaged 的類別可以有建構函式其參數具有預設值，編譯器會將它當做預設建構函式。 類別以標記`value`關鍵字不會使用建構函式使用預設值為它的參數是預設建構函式。  
  
 如需詳細資訊，請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下列範例會產生 C4534:  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```