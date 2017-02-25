---
title: "編譯器警告 (層級 3) C4823 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4823"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4823"
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器警告 (層級 3) C4823
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' 使用 Pin 指標，但沒有啟用回溯語意。請考慮使用 \/EHa  
  
 若要 Unpin 在區塊範圍中所宣告 Pin 指標指向之 Managed 堆積上的物件，編譯器會模擬區域類別的解構函式行為，「假裝」Pin 指標有可讓指標無效的解構函式。  若要在擲出例外狀況後啟用呼叫解構函式，您必須啟用物件回溯 \(作法是使用[\/EHsc](../../build/reference/eh-exception-handling-model.md)\)。  
  
 您也可以手動 Unpin 物件，並忽略警告。  
  
## 範例  
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
  
## 範例  
 使用 **\/clr:oldSyntax** 也可以產生 C4823。  下列範例會產生 C4823。  
  
```  
// C4823_b.cpp  
// compile with: /clr:oldSyntax /W3 /EHa-  
using namespace System;  
  
__gc struct G {  
   int m;  
};  
  
void f(G* pG) {  
   try {  
      int __pin* p = &pG->m;  
      // manually unpin, ignore warning  
      // p = 0;  
      throw new Exception;  
   }  
   catch(Exception*) {}  
}   // C4823  
  
int main() {  
   f( new G );  
}  
```