---
title: "編譯器警告 (層級 2) C4307 | Microsoft Docs"
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
  - "C4307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4307"
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 整數常數溢位  
  
 運算子被用於造成整數常數溢出配置空間的運算式中。  您可能需要使用較大的常數型別。  **Signed int** 能儲存的值小於 `unsigned int`，因為 **signed int** 使用一個位元代表正負號。  
  
 下列範例會產生 C4307：  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```