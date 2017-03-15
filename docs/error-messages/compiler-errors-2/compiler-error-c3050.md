---
title: "編譯器錯誤 C3050 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3050"
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1': ref 類別不可從 'type1' 繼承  
  
 `System::ValueType` 不能是參考類型的基底類別。  
  
 下列範例會產生 C3050：  
  
```  
// C3050.cpp // compile with: /clr /LD ref struct X : System::ValueType {};   // C3050 ref struct Y {};   // OK  
```