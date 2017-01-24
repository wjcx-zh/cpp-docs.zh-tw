---
title: "編譯器警告 (層級 1) C4109 | Microsoft Docs"
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
  - "C4109"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4109"
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4109
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的識別項 'identifier'  
  
 會忽略包含未預期識別項的 pragma。  
  
## 範例  
  
```  
// C4109.cpp // compile with: /W1 /LD #pragma init_seg( abc ) // C4109  
```