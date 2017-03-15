---
title: "編譯器錯誤 C2626 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2626"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2626"
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2626
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：匿名結構或等位中不允許私用或受保護的資料成員  
  
 匿名結構或等位的成員必須具有公用存取。  
  
 下列範例會產生 C2626：  
  
```  
// C2626.cpp  
int main() {  
   union {  
   protected:  
      int j;     // C2626, j is protected  
   private:  
      int k;     // C2626, k is private  
   };  
}  
```  
  
 若要修正此問題，請移除任何私用或受保護的標記：  
  
```  
// C2626b.cpp  
int main() {  
   union {  
   public:  
      int i;   // OK, i is public  
   };  
}  
```