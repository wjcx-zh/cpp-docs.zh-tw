---
title: "編譯器錯誤 C2653 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb0c1bf407d1478451c246cf615d031ef6c45bf9
ms.openlocfilehash: 2203cf8a09dbb05f6145ed238ab9fc03e458aaa5
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2653"></a>編譯器錯誤 C2653
'identifier': 不是類別或命名空間名稱  
  
語法需要類別、 結構、 等位或命名空間名稱。  
  
下列範例會產生 C2653:  
  
```cpp  
// C2653.cpp  
// compile with: /c  
class yy {  
   void func1(int i);  
};  
  
void xx::func1(int m) {}   // C2653  
void yy::func1(int m) {}   // OK  
```  
  
您也可以，如果您嘗試定義 C2653*複合的命名空間*，當您使用 Visual c + +，Visual Studio 2015 Update 3 之前的版本包含一或多個範圍巢狀命名空間名稱的命名空間。 複合命名空間定義 c + + 中不允許在 C + +&17; 之前。 從 Visual c + + 2015 Update 3 開始，編譯器支援複合的命名空間定義當[/std:c + + 最新](../../build/reference/std-specify-language-standard-version.md)編譯器選項指定︰  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++latest to fix.
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  
