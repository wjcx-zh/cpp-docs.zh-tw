---
title: "編譯器錯誤 C3553 | Microsoft Docs"
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
  - "C3553"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3553"
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3553
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

decltype 必須是運算式而不是類型  
  
 `decltype()` 關鍵字需要運算式作為引數，而不是類型名稱。 例如，下列程式碼片段的最後一個陳述式會產生錯誤 C3553。  
  
 `int x = 0;`  
  
 `decltype(x+1);`  
  
 `decltype(int); // C3553`