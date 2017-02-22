---
title: "編譯器警告 (層級 1) C4041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4041"
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制 : 瀏覽器資訊超出編譯器上限，已終止輸出  
  
 瀏覽器資訊超過編譯器限制。  
  
 這個警告可能是使用 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) \(包含區域變數的瀏覽器資訊\) 進行編譯所造成。  
  
### 使用下列可能的解決方式來進行修正  
  
1.  使用 \/Fr \(未含區域變數的瀏覽器資訊\) 進行編譯。  
  
2.  停用瀏覽器輸出 \(不使用 \/FR 或 \/Fr 進行編譯\)。