---
title: "編譯器錯誤 C2995 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2995"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2995"
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2995
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 函式樣板已經定義過了  
  
 請確定樣板類別的每個成員函式都只有一個定義。  
  
 下列範例會產生 C2995：  
  
```  
// C2995.cpp // compile with: /c template <class T> void Test(T x){} template <class T> void Test(T x){}   // C2995 template <class T> void Test2(T x){}   // OK  
```