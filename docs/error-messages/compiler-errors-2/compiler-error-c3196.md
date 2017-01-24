---
title: "編譯器錯誤 C3196 | Microsoft Docs"
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
  - "C3196"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3196"
ms.assetid: d9c38a13-191d-472d-aa2b-f61a6459d16c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3196
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword' : 使用超過一次  
  
 關鍵字使用了一次以上。  
  
 下列範例會產生 C3196：  
  
```  
// C3196.cpp  
// compile with: /clr  
ref struct R abstract abstract {};   // C3196  
ref struct S abstract {};   // OK  
```