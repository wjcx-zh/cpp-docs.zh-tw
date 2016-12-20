---
title: "編譯器錯誤 C2473 | Microsoft Docs"
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
  - "C2473"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2473"
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2473
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 類似函式定義，但沒有型式參數清單。  
  
 編譯器偵測到與函式類似的項目，但沒有參數清單。  
  
## 範例  
 下列範例會產生 C2473。  
  
```  
// C2473.cpp // compile with: /clr /c class A { int i {}   // C2473 }; class B { int i() {}   // OK };  
```