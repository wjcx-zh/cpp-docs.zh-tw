---
title: "編譯器錯誤 C2872 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2872"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2872"
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C2872
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 模稜兩可的符號  
  
 編譯器無法判斷您參考至那一個符號。  
  
 如果標頭檔包含 [using 指示詞](../../misc/using-directive-cpp.md)，而後續標頭檔也用 `#include` 包含在內，其中包含也在 `using` 指示詞中所指定命名空間中的型別，可能會發生 C2872。  請在所有標頭檔都以 `#include` 指定以後，再指定 `using` 指示詞。  
  
 如需關於C2872的詳細資訊，請參閱 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;316317](http://support.microsoft.com/default.aspx?scid=kb;en-us;316317)。  
  
 下列範例會產生 C2872：  
  
```  
// C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok  
   A::i++;   // ok  
   i++;   // C2872 ::i or A::i?  
}  
```