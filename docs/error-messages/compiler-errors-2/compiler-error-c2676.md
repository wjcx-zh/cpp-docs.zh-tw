---
title: 編譯器錯誤 C2676 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2676
dev_langs:
- C++
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffda876d8f399d3953a592d3c157b0957c7cb9a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234012"
---
# <a name="compiler-error-c2676"></a>編譯器錯誤 C2676
二元 'operator': '類型' 未定義此運算子或轉換為可接受的類型為預先定義的運算子  
  
 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2676。  
  
```  
// C2676.cpp  
// C2676 expected  
struct C {  
   C();  
} c;  
  
struct D {  
   D();  
   D operator >>( C& ){return * new D;}  
   D operator <<( C& ){return * new D;}  
} d;  
  
struct E {  
   // operator int();  
};  
  
int main() {  
   d >> c;  
   d << c;  
   E e1, e2;  
   e1 == e2;   // uncomment operator int in class E, then  
               // it is OK even though neither E::operator==(E) nor   
               // operator==(E, E) defined. Uses the conversion to int   
               // and then the builtin-operator==(int, int)  
}  
```  
  
## <a name="example"></a>範例  
 如果您嘗試在上執行指標算術 C2676 也會發生`this`參考類型的指標。  
  
 `this`指標為在參考類型的類型控制代碼。 如需詳細資訊，請參閱[語意的 this 指標](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)。  
  
 下列範例會產生 C2676。  
  
```  
// C2676_a.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct A {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
  
   A() {  
      Console::WriteLine("{0}", this + 3.3);   // C2676  
      Console::WriteLine("{0}", this[3.3]);   // OK  
   }  
};  
  
int main() {  
   A ^ mya = gcnew A();  
}  
```