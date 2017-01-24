---
title: "嚴重錯誤 C1021 | Microsoft Docs"
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
  - "C1021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1021"
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的前置處理器命令 'string'  
  
 `string` 不是有效的[前置處理器指示詞](../../preprocessor/preprocessor-directives.md)。 若要解決這個錯誤，請使用 `string` 的有效前置處理器名稱。  
  
 下列範例會產生 C1021：  
  
```  
// C1021.cpp #BadPreProcName    // C1021 delete line  
```