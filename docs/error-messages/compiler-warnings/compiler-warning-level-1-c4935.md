---
title: "編譯器警告 (層級 1) C4935 | Microsoft Docs"
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
  - "C4935"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4935"
ms.assetid: a36c56d3-571a-44dd-bb0f-bcc6b020e134
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4935
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 'access' 修改組件的存取規範  
  
 已修改類型的組件可見性。 編譯器會使用最後一個發現的規範。 例如，向前宣告的組件可見性可能會與類別定義的組件可見性不同。  
  
 僅可使用 **\/clr:oldSyntax** 連接 C4935。  
  
 下列範例會產生 C4935：  
  
```  
// C4935.cpp // compile with: /clr:oldSyntax /W1 /c public __gc public class X {   // C4935 int i; };  
```