---
title: "嚴重錯誤 C1026 | Microsoft Docs"
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
  - "C1026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1026"
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

剖析器堆疊溢位，程式太複雜  
  
 剖析程式所需的空間產生編譯器堆疊溢位。  
  
 依照下列方式減少運算式的複雜度：  
  
-   減少 `for` 和 `switch` 陳述式中的巢狀結構。  將較深的巢狀陳述式放置在個別函式。  
  
-   分割包含逗號運算子或函式呼叫 \(Function Call\) 的長運算式。