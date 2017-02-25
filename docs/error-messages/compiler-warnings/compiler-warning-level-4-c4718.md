---
title: "編譯器警告 (層級 4) C4718 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4718"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4718"
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 4) C4718
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function call': 遞迴呼叫沒有副作用，正在刪除  
  
 函式包含遞迴呼叫，但沒有副作用。 正在刪除對此函式的呼叫。 程式的正確性不受影響，但行為受影響。 因為保留呼叫可能會導致執行階段堆疊溢位的例外狀況，所以刪除該呼叫以排除這個可能性。