---
title: "編譯器錯誤 C2461 | Microsoft Docs"
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
  - "C2461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2461"
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 建構函式語法遺漏型式參數  
  
 類別的建構函式並未指定任何型式參數。  建構函式的宣告必須指定一個型式參數 \(清單可為 null\)。  
  
 請在 `class``::``class` 之後加入一對括弧。  
  
 下列範例會產生 C2461：  
  
```  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;   // C2461  
   C::C();   // OK  
};  
```