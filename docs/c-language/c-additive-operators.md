---
title: "C 加法類運算子 | Microsoft Docs"
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
  - "+ 運算子, 加法類運算子"
  - "加法類運算子"
  - "算術運算子 [C++], 加法類運算子"
  - "運算子 [C], 加法"
  - "一般算術轉換"
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 加法類運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加法類運算子會執行加法 \(**\+**\) 和減法 \(**–**\)。  
  
## 語法  
 *additive\-expression*：  
 *multiplicative\-expression*  
  
 *additive\-expression*  **\+**  *multiplicative\-expression*  
  
 *additive\-expression*  **–**  *multiplicative\-expression*  
  
> [!NOTE]
>  雖然 *additive\-expression* 的語法包括 *multiplicative\-expression*，但這並不表示需要使用乘法的運算式。  請參閱 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)中有關 *multiplicative\-expression*、*cast\-expression* 和 *unary\-expression* 的語法。  
  
 運算元可以是整數值或浮點值。  某些加法類運算也可以在指標值上執行，如每個運算子的討論中所述。  
  
 加法類運算子會對整數和浮點運算元執行一般算術轉換。  結果的類型是轉換後的運算元類型。  由於加法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果加法類運算的結果無法以運算元轉換後的類型表示，則可能會遺失資訊。  
  
## 請參閱  
 [加法類運算子：\+ 和 \-](../cpp/additive-operators-plus-and.md)