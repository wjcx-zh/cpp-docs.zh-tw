---
title: "編譯器錯誤 C2010 | Microsoft Docs"
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
  - "C2010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2010"
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'character' : 未預期在巨集型式參數清單中  
  
 這個字元在巨集定義的型式參數清單中的使用不正確。  移除該字元便可解決這種錯誤。  
  
 下列範例會產生 C2010：  
  
```  
// C2010.cpp  
// compile with: /c  
#define mymacro(a|) (2*a)   // C2010  
#define mymacro(a) (2*a)   // OK  
```