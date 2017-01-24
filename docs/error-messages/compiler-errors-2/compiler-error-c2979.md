---
title: "編譯器錯誤 C2979 | Microsoft Docs"
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
  - "C2979"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2979"
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2979
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支援在泛型中進行明確特製化  
  
 泛型類別宣告不正確。  如需詳細資訊，請參閱 [Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C2979：  
  
```  
// C2979.cpp // compile with: /clr /c generic <> ref class Utils {};   // C2979 error generic <class T> ref class Utils2 {};   // OK  
```