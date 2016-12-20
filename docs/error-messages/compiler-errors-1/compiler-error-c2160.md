---
title: "編譯器錯誤 C2160 | Microsoft Docs"
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
  - "C2160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2160"
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#\#' 不可以出現在巨集定義開頭  
  
 以語彙基元帶入的運算子 \(\#\#\) 開頭的巨集定義。  
  
 下列範例會產生 C2160：  
  
```  
// C2160.cpp // compile with: /c #define mac(a,b) #a   // OK #define mac(a,b) ##a   // C2160  
```