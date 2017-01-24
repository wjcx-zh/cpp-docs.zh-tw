---
title: "編譯器錯誤 C2118 | Microsoft Docs"
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
  - "C2118"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2118"
ms.assetid: bf4315d0-f085-4323-b813-96ee61a13bde
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2118
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

負數註標  
  
 定義陣列大小的值大於最大陣列的大小或小於零。  
  
 下列範例會產生 C2118：  
  
```  
// C2118.cpp  
int main() {  
   int array1[-1];   // C2118  
   int array2[3];   // OK  
}  
```