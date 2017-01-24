---
title: "編譯器錯誤 C2013 | Microsoft Docs"
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
  - "C2013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2013"
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遺漏 '\>'  
  
 `#include` 指示詞缺少右角括弧。 加入右角括弧，以解決錯誤。  
  
 下列範例會產生 C2013：  
  
```  
// C2013.cpp #include <stdio.h    // C2013  
```  
  
 可能的解決方式：  
  
```  
// C2013b.cpp // compile with: /c #include <stdio.h>  
```