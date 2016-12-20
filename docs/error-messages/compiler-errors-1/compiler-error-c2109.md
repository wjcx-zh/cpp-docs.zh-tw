---
title: "編譯器錯誤 C2109 | Microsoft Docs"
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
  - "C2109"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2109"
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2109
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

註標必須使用在陣列或指標型別上  
  
 註標用於非陣列的變數。  
  
 下列範例會產生 C2109：  
  
```  
// C2109.cpp  
int main() {  
   int a, b[10] = {0};  
   a[0] = 1;   // C2109  
   b[0] = 1;   // OK  
}  
```