---
title: "嚴重錯誤 C1002 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1002"
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器堆積空間不足於第二編譯階段  
  
 編譯器在第二次傳遞時用完了動態記憶體空間，可能是因為程式包含太多的符號或複雜運算式。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  將原始程式檔 \(Source File\) 分割成幾個較小的檔案。  
  
2.  將運算式打散成較小的子運算式 \(Subexpression\)。  
  
3.  移除其他消耗記憶體的程式或驅動程式。