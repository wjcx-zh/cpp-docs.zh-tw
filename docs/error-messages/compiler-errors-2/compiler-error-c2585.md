---
title: "編譯器錯誤 C2585 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2585"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2585"
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2585
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

明確轉換成 'type' 為模稜兩可  
  
 此型態轉換可能會產生一個以上的結果。  
  
### 若要修正，請檢查下列可能原因  
  
1.  從多個繼承的類別或結構型別轉換而來。  如果型別繼承相同的基底一次以上，則轉換函式或運算子必須使用範圍解析 \(`::`\) 來指定轉換中要使用哪一個繼承類別。  
  
2.  轉換運算子和建構函式已經定義為產生相同的轉換。