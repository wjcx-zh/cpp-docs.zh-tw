---
title: "巨集和 C++ | Microsoft Docs"
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
  - "巨集"
  - "巨集, C++"
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 巨集和 C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 提供的新功能，其中取代了一些由 ANSI C 前置處理器提供的功能。  這些新功能可強化此語言的類型安全及可預測性：  
  
-   在 C\+\+ 中，宣告為 **const** 的物件可在常數運算式中使用。  這可讓程式宣告具有類型和值資訊的常數，以及可以由偵錯工具以符號形式檢視的列舉。  使用前置處理器 `#define` 指示詞來定義常數會不夠精確。  除非在程式中找到取得其位址的運算式，否則不會為 **const** 物件配置儲存區。  
  
-   C\+\+ 內嵌函式功能取代了函式類型的巨集。  在巨集中使用內嵌函式的優點包括：  
  
    -   類型安全。  內嵌函式的類型檢查限制與一般函式相同。  巨集不是安全的類型。  
  
    -   修正具有副作用的引數處理。  在進入函式主體之前，內嵌函式會將所提供的運算式當做引數進行評估。  因此，沒有機會讓具有副作用的運算式不安全。  
  
 如需內嵌函式的詳細資訊，請參閱 [inline、\_\_inline、\_\_forceinline](../misc/inline-inline-forceinline.md)。  
  
 為了提供回溯相容性，Microsoft C\+\+ 會保留存在於 ANSI C 和舊版 C\+\+ 規格中的所有前置處理器功能。  
  
## 請參閱  
 [預先定義的巨集](../preprocessor/predefined-macros.md)   
 [巨集](../preprocessor/macros-c-cpp.md)