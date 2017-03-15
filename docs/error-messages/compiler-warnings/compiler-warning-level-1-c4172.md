---
title: "編譯器警告 (層級 1) C4172 | Microsoft Docs"
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
  - "C4172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4172"
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回區域變數或暫存的位址  
  
 函式會傳回區域變數或暫存物件的位址。  當函式返回時，區域變數和暫存物件會被破壞，所以傳回的位址是無效的。  
  
 請重新設計該函式，使其不再傳回區域物件 \(Local Object\) 的位址。  
  
 下列範例會產生 C4172：  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```