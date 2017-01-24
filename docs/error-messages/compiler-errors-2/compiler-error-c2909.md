---
title: "編譯器錯誤 C2909 | Microsoft Docs"
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
  - "C2909"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2909"
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2909
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 函式樣板的明確具現化必須有傳回類型  
  
 函式樣板的明確具現化必須有其傳回類型的明確規格。 隱含傳回類型規格不適用。  
  
 下列範例會產生 C2909：  
  
```  
// C2909.cpp // compile with: /c template<class T> int f(T); template f<int>(int);         // C2909 template int f<int>(int);   // OK  
```