---
title: "編譯器錯誤 C3398 | Microsoft Docs"
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
  - "C3398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3398"
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 無法從 'function\_signature' 轉換成 'function\_pointer'。 來源運算式必須是函式符號  
  
 使用 **\/clr** 編譯時，如果未指定 [\_\_clrcall](../../cpp/clrcall.md) 呼叫慣例，編譯器會為每個函式產生兩個進入點 \(位址\)：原生進入點和 Managed 進入點。  
  
 根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 \(例如，將位址指派給 `__clrcall` 函式指標時\)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。