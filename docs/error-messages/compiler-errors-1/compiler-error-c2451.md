---
title: "編譯器錯誤 C2451 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2451"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2451"
ms.assetid: a64c93a5-ab8d-4d39-ae57-9ee7ef803036
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2451
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型別 'type' 的條件式運算式不合法  
  
 條件式運算式評估為整數型別。  
  
 下列範例會產生 C2451：  
  
```  
// C2451.cpp  
class B {};  
  
int main () {  
   B b1;  
   int i = 0;  
   if (b1)   // C2451  
   // try the following line instead  
   // if (i)  
      ;  
}  
```