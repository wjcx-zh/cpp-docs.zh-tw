---
title: "編譯器警告 (層級 2) C4308 | Microsoft Docs"
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
  - "C4308"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4308"
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4308
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將負整數常數轉換為 unsigned 型別  
  
 運算式將負整數常數轉換成不帶正負號的型別。  運算式的結果可能無意義。  
  
## 範例  
  
```  
// C4308.cpp  
// compile with: /W2  
unsigned int u = (-5 + 3U);   // C4308  
  
int main()  
{  
}  
```