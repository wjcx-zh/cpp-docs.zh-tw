---
title: "多載一元運算子 | Microsoft Docs"
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
  - "遞增運算子, 多載"
  - "運算子 [C++], 一元"
  - "加號運算子"
  - "指標取值運算子多載"
  - "可重新定義的一元運算子"
  - "一元運算子"
  - "一元運算子, minus"
  - "一元運算子, plus"
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多載一元運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以多載的一元運算子如下：  
  
1.  `!` \([邏輯 NOT](../cpp/logical-negation-operator-exclpt.md)\)  
  
2.  `&` \([傳址](../cpp/address-of-operator-amp.md)\)  
  
3.  `~` \([一補數](../cpp/one-s-complement-operator-tilde.md)\)  
  
4.  `*` \([指標取值](../cpp/indirection-operator-star.md)\)  
  
5.  `+` \([一元加號](../cpp/additive-operators-plus-and.md)\)  
  
6.  `-` \([一元否定運算](../cpp/additive-operators-plus-and.md)\)  
  
7.  `++` \([遞增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\)  
  
8.  `--` \([遞減](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\)  
  
9. 轉換運算子  
  
 後置遞增和遞減運算子 \(`++` 及 **––**\) 在[遞增和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)中的處理方式不同。  
  
 轉換運算子也會在另一個主題中討論，請參閱 [轉換](../cpp/user-defined-type-conversions-cpp.md)。  
  
 下列規則對於其他所有一元運算子皆成立。  若要將一元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：  
  
 `ret-type operator` `op` `()`  
  
 其中，`ret-type` 是傳回類型，而 `op` 則是上表所列的其中一個運算子。  
  
 若要將一元運算子函式宣告為全域函式，您必須以此格式進行宣告：  
  
 `ret-type operator` `op` \(`arg` \)  
  
 其中，`ret-type` 和 `op` 是成員運算子函式，而 `arg` 則是運算類別類型的引數。  
  
> [!NOTE]
>  一元運算子的傳回類型沒有任何限制。  例如，邏輯 NOT \(`!`\) 傳回整數值是合理的，但不會強制執行。  
  
## 請參閱  
 [運算子多載](../cpp/operator-overloading.md)