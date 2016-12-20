---
title: "編譯器錯誤 C2196 | Microsoft Docs"
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
  - "C2196"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2196"
ms.assetid: fd2f6a58-48ce-4e58-96f8-e37720feb8e7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2196
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已經使用 case 值 'value'。  
  
 switch 陳述式重複使用相同的 case 值。  
  
 下列範例會產生 C2196：  
  
```  
// C2196.cpp int main() { int i = 0; switch( i ) { case 0: break; case 0:   // C2196 // try the following line instead // case 1: break; } }  
```