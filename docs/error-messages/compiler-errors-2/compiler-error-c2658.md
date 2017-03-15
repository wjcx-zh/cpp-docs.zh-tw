---
title: "編譯器錯誤 C2658 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2658"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2658"
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2658
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 在匿名結構\/等位中重複定義  
  
 兩個匿名結構或等位包含有相同識別項，但型別不同的成員宣告。  在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 之下，具有相同識別項和相同型別的成員，也會取得這項錯誤。  
  
 下列範例會產生 C2658：  
  
```  
// C2658.cpp  
// compile with: /c  
struct X {  
   union { // can be struct too  
      int i;  
   };  
   union {  
      int i;   // Under /Za, C2658  
      // int i not needed here because it is defined in the first union  
   };  
};  
  
struct Z {  
   union {  
      char *i;  
   };  
  
   union {  
      void *i;   // C2658 redefinition of 'i'  
      // try the following line instead  
      // void *ii;  
   };  
};  
```