---
title: "編譯器錯誤 C2653 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2653
dev_langs: C++
helpviewer_keywords: C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b2cca7e855256e9caf5a72e6f8b4a6e2924eca6
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
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
  
您也可以，如果您嘗試定義 C2653*複合命名空間*，當您使用 Visual c + + 在 Visual Studio 2015 Update 3 之前的版本包含一或多個範圍巢狀命名空間名稱的命名空間。 複合定義中不允許使用 c + + 在 C + + 17 之前的命名空間。 從 Visual c + + 2015 版本 15.5 開始，編譯器支援複合的命名空間定義當[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)編譯器選項指定：  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++17 to fix (or /std:c++latest in 15.3)
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  

在 Visual Studio 2017 版本 15.3，/std:c + + 最新的參數是必要。
