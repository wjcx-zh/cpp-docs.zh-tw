---
title: "編譯器錯誤 C3799 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3799"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3799"
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3799
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

索引屬性不能有空參數清單  
  
 未正確地宣告索引屬性。如需詳細資訊，請參閱[如何：使用索引屬性](../../misc/how-to-use-indexed-properties.md)。  
  
## 範例  
 下列範例會產生 C3799：  
  
```  
// C3799.cpp  
// compile with: /clr /c  
ref struct C {  
   property int default[] {   // C3799  
   // try the following line instead  
   // property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
```