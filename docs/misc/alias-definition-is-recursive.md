---
title: "Alias definition is recursive. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
當已定義能直接或間接參考本身的別名時，通常就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
1.  請變更別名的定義，然後再試一次。  
  
     \-或\-  
  
2.  在 \[命令\] 視窗輸入 `>alias`，以檢視目前別名清單和定義，然後再試一次。  
  
## 請參閱  
 [別名命令](../Topic/Alias%20Command.md)   
 [Visual Studio 命令別名](../Topic/Visual%20Studio%20Command%20Aliases.md)