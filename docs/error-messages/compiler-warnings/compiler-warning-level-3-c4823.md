---
title: "編譯器警告 （層級 3） C4823 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18e041bd9a013779a37dc2460b8e1913b69d734b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4823"></a>編譯器警告 (層級 3) C4823
'function': 使用 pin 指標但回溯語意不會啟用。 請考慮使用 /EHa  
  
若要取消釘選在區塊範圍宣告 pin 指標所指向的 managed 堆積上的物件，編譯器會模擬"偽裝"pin 指標有 nullifies 指標解構函式的本機類別的解構函式的行為。 若要啟用的解構函式的呼叫擲回例外狀況後，您必須啟用回溯的物件，您可以使用[/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
您也可以手動可以取消固定物件，並忽略此警告。  
  
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
