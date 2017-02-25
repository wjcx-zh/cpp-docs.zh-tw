---
title: "編譯器錯誤 C3715 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3715"
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'pointer' : 必須是指向 'class' 的指標  
  
 您在 [\_\_hook](../../cpp/hook.md) 或 [\_\_unhook](../../cpp/unhook.md) 指定了未指向有效類別的指標。  若要修正此錯誤，請確認您的 `__hook` 和 `__unhook` 呼叫都指定有效類別的指標。