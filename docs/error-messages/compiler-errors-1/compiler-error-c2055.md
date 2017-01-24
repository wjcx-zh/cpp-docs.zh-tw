---
title: "編譯器錯誤 C2055 | Microsoft Docs"
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
  - "C2055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2055"
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須是型式參數清單，而非型別清單  
  
 函式定義中包含了參數型別清單，而非型式參數清單 \(Formal Parameter List\)。  ANSI C 要求型式參數必須為具名參數，除非它們為虛值 \(Void\) 或是省略 \(`...`\)。  
  
 下列範例會產生 C2055：  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```