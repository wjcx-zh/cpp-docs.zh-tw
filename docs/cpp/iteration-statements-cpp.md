---
title: "反覆運算陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "反覆運算陳述式"
  - "迴圈結構, 反覆運算陳述式"
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 反覆運算陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反覆項目陳述式會使陳述式 \(或複合陳述式\) 依據某種迴圈終止準則執行零次或多次。  如果這些陳述式是複合陳述式，除非遇到 [break](../cpp/break-statement-cpp.md) 陳述式或 [continue](../cpp/continue-statement-cpp.md) 陳述式，否則它們會依順序執行。  
  
 C\+\+ 提供四個反覆項目陳述式：[while](../cpp/while-statement-cpp.md)、[do](../cpp/do-while-statement-cpp.md)、[for](../cpp/for-statement-cpp.md) 和 [range\-based for](../cpp/range-based-for-statement-cpp.md)。  這些陳述式中每一個都會反覆執行，直到其終止運算式判斷值為零 \(false\)，或是使用 **break** 陳述式強制終止迴圈為止。  下表摘要說明這些陳述式及它們的動作，而且每一個陳述式會在後續章節中詳細討論。  
  
### 反覆項目陳述式  
  
|陳述式|評估位置|初始化|遞增|  
|---------|----------|---------|--------|  
|`while`|迴圈頂端|否|否|  
|**do**|迴圈底部|否|否|  
|**for**|迴圈頂端|是|是|  
|**範圍架構的 for**|迴圈頂端|是|是|  
  
 反覆項目陳述式的陳述式部分不可以是宣告。  不過，它可以是包含宣告的複合陳述式。  
  
## 請參閱  
 [C\+\+ 陳述式概觀](../cpp/overview-of-cpp-statements.md)