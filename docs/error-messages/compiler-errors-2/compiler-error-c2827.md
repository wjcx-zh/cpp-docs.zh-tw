---
title: "編譯器錯誤 C2827 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2827"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2827"
ms.assetid: cb3e5814-0c92-40e4-b620-98578ae3003a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2827
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operator' 不可以使用一元形式進行全域覆寫  
  
 物件外的運算子不能有一元型式。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  使多載運算子成為物件的區域成員。  
  
2.  選擇適當的一元運算子來多載。