---
title: "編譯器警告 (層級 3) C4554 | Microsoft Docs"
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
  - "C4554"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4554"
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4554
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 檢查運算子優先順序找出可能發生的錯誤; 使用括號釐清順序  
  
 下列範例會產生 C4554：  
  
```  
// C4554.cpp  
// compile with: /W3 /WX  
int main() {  
   int a = 0, b = 0, c = 0;  
   a = a << b + c;   // C4554  
   // probably intended (a << b) + c,  
   // but will get a << (b + c)  
}  
```