---
title: "具有一元運算子的運算式 | Microsoft Docs"
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
  - "運算式 [C++], 運算子"
  - "運算式 [C++], 一元運算子"
  - "一元運算子, 運算式具有"
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 具有一元運算子的運算式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一元運算子只會在運算式中的一個運算元上作用。  一元運算子如下：  
  
-   [間接運算子 \(\*\)](../cpp/indirection-operator-star.md)  
  
-   [傳址運算子 \(&\)](../cpp/address-of-operator-amp.md)  
  
-   [一元加號運算子 \(\+\)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [一元負運算子 \(–\)](../misc/unary-negation-operator.md)  
  
-   [邏輯負運算子 \(\!\)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [一補數運算子 \(~\)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [前置遞增運算子 \(\+\+\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [前置遞減運算子 \(––\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [轉型運算子 \(\)](../cpp/cast-operator-parens.md)  
  
-   [sizeof 運算子](../cpp/sizeof-operator.md)  
  
-   [\_\_uuidof 運算子](../cpp/uuidof-operator.md)  
  
-   [\_\_alignof 運算子](../cpp/alignof-operator.md)  
  
-   [new 運算子](../cpp/new-operator-cpp.md)  
  
-   [delete 運算子](../cpp/delete-operator-cpp.md)  
  
 這些運算子具有由右到左的順序關聯性。  一元運算式的語法通常會置於後置或主要運算式的前方。  
  
 以下是一元運算式的可能形式。  
  
-   *postfix\-expression*  
  
-   `++` *unary\-expression*  
  
-   `––` *unary\-expression*  
  
-   *unary\-operator* *cast\-expression*  
  
-   `sizeof` *unary\-expression*  
  
-   `sizeof(` *type\-name* `)`  
  
-   `decltype(` *expression* `)`  
  
-   *allocation\-expression*  
  
-   *deallocation\-expression*  
  
 所有 *postfix\-expression* 皆視為 *unary\-expression*，因為任何主要運算式皆視為 *postfix\-expression*，所以任何的主要運算式也都視為 *unary\-expression*。  如需詳細資訊，請參閱[後置運算式](../cpp/postfix-expressions.md)和[主要運算式](../cpp/primary-expressions.md)。  
  
 *unary\-operator* 由一個或多個下列符號組成：`* &` `+` `–` `!` `~`  
  
 *cast\-expression* 是可以選用轉換類型的一元運算式。  如需詳細資訊，請參閱[轉換運算子：\(\)](../cpp/cast-operator-parens.md)。  
  
 *expression* 可以是任何運算式。  如需詳細資訊，請參閱[運算式](../cpp/expressions-cpp.md)。  
  
 *allocation\-expression* 意指 `new` 運算子。  *deallocation\-expression* 意指 `delete` 運算子。  如需詳細資訊，請參閱本主題稍早的連結。  
  
## 請參閱  
 [運算式的類型](../cpp/types-of-expressions.md)