---
title: "編譯器警告 (層級 1) C4237 | Microsoft Docs"
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
  - "C4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4237"
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目前尚未支援 'keyword' 關鍵字，但保留供將來使用  
  
 C\+\+ 規格中的關鍵字不是在 Visual C\+\+ 編譯器中實作，但關鍵字無法以使用者定義的符號提供使用。  
  
 下列範例會產生 C4237：  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```