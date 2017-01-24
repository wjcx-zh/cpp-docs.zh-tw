---
title: "編譯器錯誤 C2466 | Microsoft Docs"
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
  - "C2466"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2466"
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2466
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法配置常數大小為 0 的陣列  
  
 配置或宣告一個大小為零的陣列。  陣列大小的常數運算式必須是大於零的整數。  註標 \(Subscript\) 為零的陣列宣告只能用於類別、結構或等位的成員，並只能在具有 Microsoft 擴充功能 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\) 時使用。  
  
 下列範例會產生 C2466：  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```