---
title: "嚴重錯誤 C1852 | Microsoft Docs"
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
  - "C1852"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1852"
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1852
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' 是無效的先行編譯標頭檔  
  
 檔案不是先行編譯標頭檔。  
  
### 透過檢查下列可能原因進行修正  
  
1.  使用 **\/Yu** 或 **\#pragma hdrstop** 指定的檔案無效。  
  
2.  如果您未指定副檔名，編譯器會假設副檔名為 .pch。