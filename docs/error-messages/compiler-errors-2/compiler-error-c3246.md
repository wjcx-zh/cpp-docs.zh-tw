---
title: "編譯器錯誤 C3246 | Microsoft Docs"
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
  - "C3246"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3246"
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3246
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': 無法繼承自 'type'，因為它已經宣告為 'sealed'  
  
 標示為 [sealed](../../misc/sealed.md) 的類別不能當成任何其他類別的基底類別。  
  
 下列範例會產生 C3246：  
  
```  
// C3246_2.cpp // compile with: /clr /LD ref class X sealed {}; ref class Y : public X {}; // C3246  
```  
  
 下列範例會產生 C3246：  
  
```  
// C3246.cpp // compile with: /clr:oldSyntax /LD #using <mscorlib.dll> __sealed __gc class X {}; __gc class Y : public X {}; // C3246  
```