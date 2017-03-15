---
title: "嚴重錯誤 C1190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1190"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1190"
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 嚴重錯誤 C1190
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Managed 目標程式碼需要 '\/clr' 選項  
  
 您使用 CLR 建構，但未指定 **\/clr**。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下列範例會產生 C1190：  
  
```  
// C1190.cpp // compile with: /c __gc class A {};   // C1190 ref class A {};  
```