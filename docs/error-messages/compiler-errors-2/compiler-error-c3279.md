---
title: "編譯器錯誤 C3279 | Microsoft Docs"
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
  - "C3279"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3279"
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3279
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cli 命名空間中宣告的類別樣板，不允許部分和明確特製化以及明確具現化  
  
 `cli` 命名空間由 Microsoft 所定義，並包含虛擬範本。 在這個命名空間中，Visual C\+\+ 編譯器不允許使用者定義的部分和明確特製化，以及類別樣板的明確具現化。  
  
 下列範例會產生 C3279：  
  
```  
// C3279.cpp // compile with: /clr namespace cli { template <> ref class array<int> {};   // C3279 template <typename T> ref class array<T, 2> {};   // C3279 }  
```