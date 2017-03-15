---
title: "轉型運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉型運算子"
  - "運算子 [C++], 轉型"
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 轉型運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 語言有幾個特有的轉型運算子。  這些運算子的目的在於移除舊式 C 語言轉型固有的模稜兩可和危險。  這些運算子如下所列：  
  
-   用於轉換多型類型的 [dynamic\_cast](../cpp/dynamic-cast-operator.md)。  
  
-   用於轉換非多型類型的 [static\_cast](../cpp/static-cast-operator.md)。  
  
-   用來移除 `const`、`volatile` 和 `__unaligned` 屬性的 [const\_cast](../cpp/const-cast-operator.md)。  
  
-   用於位元簡單重新定義的 [reinterpret\_cast](../cpp/reinterpret-cast-operator.md)。  
  
-   用於產生可驗證 MSIL 的 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 `const_cast` 和 `reinterpret_cast` 建議做為最後手段使用，因為這些運算子與舊類型轉換存在相同危險。  然而，為了完全取代舊類型轉換，這些運算子仍有其必要。  
  
## 請參閱  
 [轉型](../cpp/casting.md)