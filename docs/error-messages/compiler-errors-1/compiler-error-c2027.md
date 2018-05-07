---
title: 編譯器錯誤 C2027 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be3c85d2ffbd3fffe4e1e6ce6dafc615f199c00a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2027"></a>編譯器錯誤 C2027
使用未定義類型 'type'  
  
 其定義之前，無法使用型別。 若要解決此錯誤，請確定類型已完整定義之前正在參照它。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2027。  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>範例  
 它可宣告宣告但未定義類型的指標。  但是 Visual c + + 不允許參考未定義的類型。  
  
 下列範例會產生 C2027。  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```