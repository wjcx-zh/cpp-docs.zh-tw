---
title: "編譯器錯誤 C2241 | Microsoft Docs"
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
  - "C2241"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2241"
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2241
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 成員存取受限制  
  
 程式碼嘗試存取私用或受保護的成員。  
  
### 使用下列可能的解決方式來進行修正  
  
1.  變更成員的存取層級。  
  
2.  宣告成員為存取函式的 `friend`。