---
title: "編譯器錯誤 C2588 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2588"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2588"
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2588
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'::~identifier' : 不合法的全域解構函式  
  
 此解構函式是針對類別、結構或等位以外的項目而定義的。  這是不允許的。  
  
 這項錯誤可能是因範圍解析 \(`::`\) 運算子左邊遺漏類別、結構或等位名稱所致。  
  
 下列範例會產生 C2588：  
  
```  
// C2588.cpp  
~F();   // C2588  
```