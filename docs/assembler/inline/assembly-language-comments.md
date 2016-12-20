---
title: "組合語言註解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 指示"
  - "組件語言 [C++], 註解"
  - "註解 [C++], 組件語言"
  - "巨集 [C++], 組件語言"
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 組合語言註解
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 指示`__asm`區塊可以使用組件語言的註解:  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 由於 C 的巨集展開成單一邏輯行，請避免在巨集中使用組件語言的註解。  \(請參閱[定義視為 C 巨集的 \_\_asm 區塊](../../assembler/inline/defining-asm-blocks-as-c-macros.md)。\)  `__asm`區塊也可以包含 C 樣式註解; 如需詳細資訊，請參閱[使用 C 或 c \+ \+ \_\_asm 區塊中的](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)。  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)