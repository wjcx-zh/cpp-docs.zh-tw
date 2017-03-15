---
title: "C++ 標點符號 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - ";"
  - ","
  - "{"
  - "}"
  - "("
  - ")"
  - "["
  - "]"
  - "!"
  - "%"
  - "^"
  - "*"
  - """
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "標點符號"
ms.assetid: 1521564c-a977-488a-9490-068079897592
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 標點符號
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 中的標點符號對於編譯器具有語法和語意上的含意，但本身並不指定產生值的作業。  不論是單獨或組合，有些標點符號也可以是 C\+\+ 運算子，或對前置處理器具有重大意義。  
  
 下列任何字元皆視為標點符號：  
  
```  
! % ^ & * ( ) – + = { } | ~  
[ ] \ ; ' : " < > ? , . / #  
```  
  
 標點符號 **\[ \]**、**\( \)** 和 **{ }** 必須以配對形式出現在[轉譯階段](../preprocessor/phases-of-translation.md) 4 之後。  
  
## 請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)