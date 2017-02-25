---
title: "嚴重錯誤 C1210 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1210"
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 嚴重錯誤 C1210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所安裝的執行階段版本不支援 \/clr:pure 和 \/clr:safe  
  
 如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1210。  
  
 編譯器的某個功能可能無法在執行階段的舊版本上運作。  
  
 若要解決 C1210，請安裝要與編譯器搭配使用的 Common Language Runtime 版本。