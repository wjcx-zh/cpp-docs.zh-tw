---
title: "編譯器警告 C4959 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4959
dev_langs:
- C++
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f7cde1151bd220415b950dcce089265be118de34
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4959"></a>編譯器警告 C4959
無法在 /clr:safe 中定義 Unmanaged 結構 'type'，因為存取它的成員會產生無法驗證的程式碼  
  
 存取 Unmanaged 類型的成員將會產生無法驗證的 (peverify.exe) 映像。  
  
 如需詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 這個警告就會發出為錯誤，而且可以停用與[警告](../../preprocessor/warning.md)pragma 或[/wd](../../build/reference/compiler-option-warning-level.md)編譯器選項。  
  
 下列範例會產生 C4959：  
  
```  
// C4959.cpp  
// compile with: /clr:safe  
  
// Uncomment the following line to resolve.  
// #pragma warning( disable : 4959 )  
struct X {  
   int data;  
};  
  
int main() {  
   X x;  
   x.data = 10;   // C4959  
}  
```
