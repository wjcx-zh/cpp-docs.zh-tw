---
title: "編譯器警告 (層級 4) C4389 | Microsoft Docs"
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
  - "c4389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4389"
ms.assetid: fc0e3a8e-f766-437c-b7f1-e61abb2a8765
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4389
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : signed\/unsigned 不相符  
  
 作業中包含帶正負號和不帶正負號的變數。  這會造成資料的遺漏。  
  
 下列範例會產生 C4389：  
  
```  
// C4389.cpp  
// compile with: /W4  
#pragma warning(default: 4389)  
  
int main()  
{  
   int a = 9;  
   unsigned int b = 10;  
   if (a == b)   // C4389  
      return 0;  
   else  
      return 0;  
};  
```