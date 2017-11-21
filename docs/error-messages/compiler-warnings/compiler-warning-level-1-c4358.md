---
title: "編譯器警告 （層級 1） C4358 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4358
dev_langs: C++
helpviewer_keywords: C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f09125123ea075c1d0c9fbce5fdd432dfa64407
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4358"></a>編譯器警告 (層級 1) C4358
'operator': 傳回組合委派的類型不是 'void';傳回的值會是未定義  
  
 已合併兩個委派，並傳回值不是 void。 如果兩個委派具有非 void 傳回值結合時，編譯器會無法執行適當的設定，如果使用委派的傳回值。  
  
 下列範例會產生 C4358:  
  
```  
// C4358.cpp  
// compile with: /clr /W1  
delegate int D();  
delegate void E();  
  
ref class X {  
   int i;  
public:  
   X(int ii) : i(ii) {}  
   int f() {  
      return i;  
   }  
};  
  
ref class Y {  
   int i;  
public:  
   Y() {}  
   void g() {}  
};  
  
int main() {  
   D^ d = gcnew D(gcnew X(1), &X::f);  
   D^ d2 = gcnew D(gcnew X(2), &X::f);  
  
   d += d2;   // C4358  
   int j = d();   // return value indeterminate  
  
   E^ e = gcnew E(gcnew Y, &Y::g);  
   E^ e2 = gcnew E(gcnew Y, &Y::g);  
   e += e2;   // OK  
}  
```