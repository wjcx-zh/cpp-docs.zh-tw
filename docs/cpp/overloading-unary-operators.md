---
title: "多載一元運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d124410b785e44a9dcb55890b4723ebbae2da56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overloading-unary-operators"></a>多載一元運算子
可以多載的一元運算子如下：  
  
1.  `!`([邏輯 NOT](../cpp/logical-negation-operator-exclpt.md))  
  
2.  `&`([傳址](../cpp/address-of-operator-amp.md))  
  
3.  `~`([一補數](../cpp/one-s-complement-operator-tilde.md))  
  
4.  `*`([指標取值 （dereference)](../cpp/indirection-operator-star.md))  
  
5.  `+`([一元加號](../cpp/additive-operators-plus-and.md))  
  
6.  `-`([一元否定運算](../cpp/additive-operators-plus-and.md))  
  
7.  `++`([遞增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
8.  `--`([遞減](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))  
  
9. 轉換運算子  
  
 後置遞增和遞減運算子 (`++`和 **--** ) 中需分開處理[遞增和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)。  
  
 轉換運算子也會討論不同的主題。請參閱[使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)。  
  
 下列規則對於其他所有一元運算子皆成立。 若要將一元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：  
  
 `ret-type operator` `op` `()`  
  
 其中，`ret-type` 是傳回類型，而 `op` 則是上表所列的其中一個運算子。  
  
 若要將一元運算子函式宣告為全域函式，您必須以此格式進行宣告：  
  
 `ret-type operator` `op` (`arg` )  
  
 其中，`ret-type` 和 `op` 是成員運算子函式，而 `arg` 則是運算類別類型的引數。  
  
> [!NOTE]
>  一元運算子的傳回類型沒有任何限制。 例如，邏輯 NOT (`!`) 傳回整數值是合理的，但不會強制執行。  
  
## <a name="see-also"></a>請參閱  
 [運算子多載](../cpp/operator-overloading.md)