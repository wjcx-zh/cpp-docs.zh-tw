---
title: "abort 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort 函式"
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# abort 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**abort** 函式也是在標準 Include 檔案 STDLIB.H 中宣告，此函式會終止 C\+\+ 程式。  **exit** 與 **abort** 間的差異在於，**exit** 允許執行 C\+\+ 執行階段終止處理 \(將會呼叫全域物件解構函式\)，而 **abort** 則會立即終止程式。  如需詳細資訊，請參閱《執行階段程式庫參考》中的 [abort](../c-runtime-library/reference/abort.md)。  
  
## 請參閱  
 [程式終止](../cpp/program-termination.md)