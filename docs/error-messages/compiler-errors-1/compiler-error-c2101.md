---
title: "編譯器錯誤 C2101 | Microsoft Docs"
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
  - "C2101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2101"
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2101
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不可在常數上使用 '&'  
  
 傳址運算子 \(`&`\) 必須將左值 \(l\-value\) 作為運算元。  
  
 下列範例會產生 C2101：  
  
```  
// C2101.cpp int main() { char test; test = &'a';   // C2101 test = 'a';   // OK }  
```