---
title: "編譯器錯誤 C3556 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3556"
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'expression': 'decltype' 的引數不正確  
  
 編譯器無法減少 `decltype(``expression``)` 類型規範之引數的運算式類型。 在下列程式碼範例中，編譯器無法減少 `myFunction` 引數的類型，因為 `myFunction` 多載。  
  
```  
void myFunction(); void myFunction(int); decltype(myFunction); // C3556  
```