---
title: "編譯器警告 (層級 4) C4670 | Microsoft Docs"
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
  - "C4670"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4670"
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4670
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 此基底類別無法存取  
  
 無法存取要在 **try** 區塊中擲回之物件的指定基底類別。 如果擲回物件，則無法具現化物件。 請檢查使用正確的存取規範來繼承基底類別。  
  
 下列範例會產生 C4670：  
  
```  
// C4670.cpp // compile with: /EHsc /W4 class A { }; class B : /* public */ A { } b;   // inherits A with private access by default int main() { try { throw b;   // C4670 } catch( B ) { } }  
```