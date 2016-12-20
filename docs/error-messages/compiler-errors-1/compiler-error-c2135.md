---
title: "編譯器錯誤 C2135 | Microsoft Docs"
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
  - "C2135"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2135"
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2135
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'bit operator': 不合法的位元欄位運算  
  
 傳址運算子 \(`&`\) 無法套用至位元欄位。  
  
 下列範例會產生 C2135：  
  
```  
// C2135.cpp struct S { int i : 1; }; struct T { int j; }; int main() { &S::i;   // C2135 address of a bit field &T::j;   // OK }  
```