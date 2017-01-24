---
title: "編譯器錯誤 C3554 | Microsoft Docs"
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
  - "C3554"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3554"
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3554
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'decltype' 無法和任何其他型別規範結合  
  
 您不能限制 `decltype()` 關鍵字搭配任何類型規範。 例如，下列程式碼片段會產生錯誤 C3554。  
  
```  
int x; unsigned decltype(x); // C3554  
```