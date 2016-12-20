---
title: "編譯器錯誤 C3455 | Microsoft Docs"
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
  - "C3455"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3455"
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3455
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': 沒有任何屬性建構函式與引數相符  
  
 用來宣告屬性的值無效。  如需詳細資訊，請參閱 [attribute](../../windows/attribute.md)。  
  
## 範例  
 下列範例會產生 C3455。  
  
```  
// C3455.cpp // compile with: /clr /c using namespace System; [attribute("MyAt")]   // C3455 // try the following line instead // [attribute(All)] ref struct MyAttr { MyAttr() {} };  
```