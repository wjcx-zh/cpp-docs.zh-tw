---
title: 編譯器錯誤 C2079 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2079
dev_langs:
- C++
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b29200be08c10dcfaeb178941309c6f3aec6ff9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2079"></a>編譯器錯誤 C2079
'identifier' 會使用未定義的類別/結構/等位 'name'  
  
 指定的識別項是未定義的類別、 結構或等位。  
  
 這個錯誤可能被因初始化匿名等位。  
  
 下列範例會產生 C2079:  
  
```  
// C2079.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   std::ifstream g;   // C2079  
}  
```  
  
 可能的解決方式：  
  
```  
// C2079b.cpp  
// compile with: /EHsc  
#include <fstream>  
int main( ) {  
   std::ifstream g;  
}  
```  
  
 如果您嘗試將其向前宣告是只能在範圍中之型別的堆疊上宣告物件時，也會發生 C2079。  
  
```  
// C2079c.cpp  
class A;  
  
class B {  
   A a;   // C2079  
};  
  
class A {};  
```  
  
 可能的解決方式：  
  
```  
// C2079d.cpp  
// compile with: /c  
class A;  
class C {};  
  
class B {  
   A * a;  
   C c;  
};  
  
class A {};  
```