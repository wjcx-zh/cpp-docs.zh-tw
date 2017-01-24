---
title: "編譯器錯誤 C3087 | Microsoft Docs"
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
  - "C3087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3087"
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'named\_argument: 'attribute' 的呼叫已將此成員初始化  
  
 具名引數指定在與相同值之未命名引數的相同屬性區塊中。 請只指定具名或未命名的引數。  
  
## 範例  
 下列範例會產生 C3087：  
  
```  
// C3087.cpp // compile with: /c [idl_quote("quote1", text="quote2")];   // C3087 [idl_quote(text="quote3")];   // OK [idl_quote("quote4")];   // OK  
```