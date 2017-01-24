---
title: "編譯器錯誤 C2736 | Microsoft Docs"
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
  - "C2736"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2736"
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2736
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換中不允許有 'keyword' 關鍵字  
  
 關鍵字在此型別轉換中是無效的。  
  
 下列範例會產生 C2736：  
  
```  
// C2736.cpp  
int main() {  
   return (virtual) 0;   // C2736  
   // try the following line instead  
   // return 0;  
}  
```