---
title: "編譯器警告 (層級 4) C4057 | Microsoft Docs"
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
  - "C4057"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4057"
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4057
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 'identifier1' 在間接取值上與 'identifier2' 的基底類型有些許不同  
  
 兩個指標運算式參考不同的基底類型。 運算式使用時沒有轉換。  
  
### 透過檢查下列可能原因進行修正  
  
1.  混合帶正負號和不帶正負號的類型。  
  
2.  混合了 **short** 和 **long** 類型。