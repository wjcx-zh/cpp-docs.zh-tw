---
title: "編譯器錯誤 C2885 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2885
dev_langs: C++
helpviewer_keywords: C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a19f209d53d7d0b37cddbf559fa3dc02ee50db7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2885"></a>編譯器錯誤 C2885
'class::identifier': 不正確使用宣告在非類別範圍  
  
 您使用[使用](../../cpp/using-declaration.md)宣告不正確。  
  
## <a name="example"></a>範例  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致這個錯誤： 已不再有效有`using`宣告，以巢狀類型; 您必須明確限定您對巢狀類型，將型別放在名稱中的每個參考空間，或建立 typedef。  
  
 下列範例會產生 C2885。  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## <a name="example"></a>範例  
 如果您使用`using`類別成員，c + + 關鍵字必須要定義該成員存在於其他類別 （衍生的類別）。  
  
 下列範例會產生 C2885。  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```