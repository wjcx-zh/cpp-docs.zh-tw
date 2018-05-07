---
title: 編譯器錯誤 C2108 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2108
dev_langs:
- C++
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 066cb589b81223085f0ced589695eb3cda4c5fea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2108"></a>編譯器錯誤 C2108
註標不是整數類資料類型  
  
 陣列註標是的是非整數運算式。  
  
## <a name="example"></a>範例  
 如果您不當使用，可能會發生 C2108`this`存取類型的預設索引子的實值類型的指標。 如需詳細資訊，請參閱[語意的 this 指標](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。  
  
 下列範例會產生 C2108。  
  
```  
// C2108.cpp  
// compile with: /clr  
using namespace System;  
  
value struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
   void Test() {  
      Console::WriteLine("{0}", this[3.3]);   // C2108  
      Console::WriteLine("{0}", this->default[3.3]);   // OK  
   }  
};  
  
int main() {  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```