---
title: "編譯器錯誤 C2790 | Microsoft Docs"
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
  - "C2790"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2790"
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2790
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'super': 此關鍵字只在類別成員函式的主體使用  
  
 如果使用者曾嘗試於成員函式外使用 [super](../../cpp/super.md) 關鍵字，則會出現這項錯誤訊息。  
  
 下列範例會產生 C2790：  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```