---
title: "編譯器錯誤 C2388 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2388"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2388"
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C2388
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 符號不可同時以 \_\_declspec\(appdomain\) 和 \_\_declspec\(process\) 宣告  
  
 `appdomain` 和 `process` `__declspec` 修飾詞不能用在相同的符號上。 變數的儲存體依處理序或應用程式定義域而存在。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和[處理序](../../cpp/process.md)。  
  
 下列範例會產生 C2388：  
  
```  
// C2388.cpp // compile with: /clr /c __declspec(process) __declspec(appdomain) int i;   // C2388 __declspec(appdomain) int i;   // OK  
```