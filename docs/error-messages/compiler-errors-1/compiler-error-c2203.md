---
title: "編譯器錯誤 C2203 | Microsoft Docs"
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
  - "C2203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2203"
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除運算子無法指定陣列的界限  
  
 指定 **\/Za** \(ANSI\) 選項時，`delete` 運算子可刪除整個陣列，但不能刪除陣列的部分或特定成員。  
  
 下列範例會產生 C2203：  
  
```  
// C2203.cpp  
// compile with: /Za  
int main() {  
   int *ar = new int[10];  
   delete [4] ar;   // C2203  
   // try the following line instead  
   // delete [] ar;  
}  
```