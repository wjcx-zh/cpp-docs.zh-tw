---
title: "編譯器錯誤 C2014 | Microsoft Docs"
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
  - "C2014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2014"
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前置處理器命令前不可有非空白的字元  
  
 前置處理器指示詞 \(Preprocessor Directive\) 的 `#` 符號必須為非空白行中的第一個字元。  
  
 下列範例會產生 C2014：  
  
```  
// C2014.cpp  
int k; #include <stdio.h>   // C2014  
```  
  
 可能的解決方案：  
  
```  
// C2014b.cpp  
// compile with: /c  
int k;   
#include <stdio.h>  
```