---
title: "編譯器警告 (層級 1) C4729 | Microsoft Docs"
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
  - "C4729"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4729"
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4729
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

依據 flow graph 產生的警告，發現函式太大  
  
 如果要編譯的函式太大，無法可靠地檢查將產生警告的情況，則會產生這個警告。 使用 [\/Od](../../build/reference/od-disable-debug.md) 編譯器選項時，才會產生這個警告。  
  
 若要解決這個警告，請將函式分為較小的函式。