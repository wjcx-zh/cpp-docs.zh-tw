---
title: "前置處理器運算子 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "運算子 [C++], 前置處理器"
  - "前置處理器運算子"
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 前置處理器運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

四個前置處理器特定運算子使用 `#define` 指示詞中 \(為中的每一個摘要參閱下列清單\)。  stringizing， charizing 和語彙基元貼上運算子在下個章節中討論。  如需 **defined** 運算子的詳細資訊，請參閱 [\#if、和 \#elif \#else 指示詞 \#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
|運算子|動作|  
|---------|--------|  
|[字串化運算子 \(\#\)](../preprocessor/stringizing-operator-hash.md)|以雙引號將實際對應的引數括住|  
|[字元化運算子 \(\#@\)](../preprocessor/charizing-operator-hash-at.md)|以單引號造成對應的引數會將和視為字元 \(Microsoft 專用\)|  
|[語彙基元帶入的運算子 \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md)|允許做為實際引數的語彙基元會串連形成其他語彙基元|  
|[DEFINED 運算子](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|簡化的語式是否正確文字在某些巨集的指示詞|  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)   
 [預先定義的巨集](../preprocessor/predefined-macros.md)   
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)