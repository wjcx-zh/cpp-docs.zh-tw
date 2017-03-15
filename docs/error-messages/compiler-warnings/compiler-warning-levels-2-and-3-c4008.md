---
title: "編譯器警告 (層級 2 和 3) C4008 | Microsoft Docs"
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
  - "C4008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4008"
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2 和 3) C4008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 已忽略 'attribute' 屬性  
  
 編譯器已忽略函式 \(層級 3 警告\) 或資料 \(層級 2 警告\) 的 `__fastcall`、**static** 或 **inline** 屬性。  
  
### 透過檢查下列可能原因進行修正  
  
1.  具有資料的 `__fastcall` 屬性。  
  
2.  具有 **main** 函式的 **static** 或 **inline** 屬性。