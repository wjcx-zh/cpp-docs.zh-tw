---
title: "編譯器錯誤 C2130 | Microsoft Docs"
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
  - "C2130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2130"
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line 必須有包含檔名的字串，但只找到 'token'  
  
 [\#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 後面的選擇性檔名語彙基元必須是字串。  
  
 下列範例會產生 C2130：  
  
```  
// C2130.cpp int main() { #line 1000 test   // C2130 #line 1000 "test"   // OK }  
```