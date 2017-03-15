---
title: "編譯器錯誤 C2019 | Microsoft Docs"
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
  - "C2019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2019"
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須是前置處理器指示詞，但找到 'character'  
  
 跟在 `#` 符號後面的字元並非前置處理器指示詞的第一個字元。  
  
 下列範例會產生 C2019：  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 可能的解決方案：  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```