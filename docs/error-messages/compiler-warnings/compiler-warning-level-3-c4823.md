---
title: "編譯器警告 （層級 3） C4823 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 12
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ea03723f9ccae2348a47ae4894097f5cd9f8b5a1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4823"></a>編譯器警告 (層級 3) C4823
'function': 使用 pin 指標但回溯語意 （semantics） 不會啟用。 請考慮使用 /EHa  
  
若要取消釘選在區塊範圍中宣告 pin 指標在 managed 堆積上的物件，編譯器會模擬本機 「 假裝 」 pin 指標具有 nullifies 指標解構函式類別的解構函式的行為。 若要啟用的解構函式呼叫之後擲回例外狀況，您必須啟用物件復原時，您可以使用進行[/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
您也可以手動取消固定物件和忽略的警告。  
  
## <a name="example"></a>範例  
下列範例會產生 C4823。  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  

