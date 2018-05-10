---
title: C 常數運算式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaeb7ab79777d247f0bc0b2e6d749d8df5a7f8e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="c-constant-expressions"></a>C 常數運算式
常數運算式會在編譯時期評估，而不是在執行階段評估，而且可用於可以使用常數的任何位置。 常數運算式必須評估為常數，並且必須在該類型可顯示值的範圍內。 常數運算式的運算元可以是整數常數、字元常數、浮點常數、列舉常數、類型轉換、`sizeof` 運算式和其他常數運算式。  
  
## <a name="syntax"></a>語法  
 *constant-expression*：  
 *conditional-expression*  
  
 *conditional-expression*：  
 *logical-OR-expression*  
  
 *logical-OR-expression* **?**  *expression* **:**  *conditional-expression*  
  
 *expression*：  
 *assignment-expression*  
  
 *expression* **,**  *assignment-expression*  
  
 *assignment-expression*：  
 *conditional-expression*  
  
 *unary-expression assignment-operator assignment-expression*  
  
 *assignment-operator*：下列其中一個  
 **= \*= /= %= += -= <\<= >>= &= ^= &#124;=**  
  
 結構宣告子、列舉程式、直接宣告子、直接抽象宣告子和標記陳述式包含 *constant-expression* 非終端項。  
  
 必須使用整數常數運算式指定結構的位元欄位成員、列舉常數的值、陣列的大小或 **case** 常數的值。  
  
 前置處理器指示詞中所使用的常數運算式必須遵守其他限制。 因此，這些運算式稱為「受限制的常數運算式」。 受限制的常數運算式不能包含 `sizeof` 運算式、列舉常數、任何類型的類型轉換，或浮點類型常數。 不過，此類運算式可以包含特殊常數運算式 `defined (`*identifier*`)`。  
  
## <a name="see-also"></a>請參閱  
 [運算元和運算式](../c-language/operands-and-expressions.md)