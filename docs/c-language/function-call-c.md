---
title: 函式呼叫 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49c9483cb6e556d5a8b174377c0dad666834c9e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="function-call-c"></a>函式呼叫 (C)
「函式呼叫」是運算式，其中包含所呼叫函式的名稱，或函式指標的值，以及傳遞至函式的選擇性引數。  
  
## <a name="syntax"></a>語法  
 *postfix-expression*：  
 *postfix-expression*  **(**  *argument-expression-list* opt **)**  
  
 *argument-expression-list*：  
 *assignment-expression*  
  
 *argument-expression-list*  **,**  *assignment-expression*  
  
 *postfix-expression* 必須評估為函式位址 (例如，函式識別項或函式指標的值)，而 *argument-expression-list* 是運算式的清單 (以逗號分隔)，其中的值 (引數) 會傳遞至函式。 *argument-expression-list* 引數可以是空的。  
  
 函式呼叫運算式具有函式傳回值的值和類型。 函式不能傳回陣列類型的物件。 如果函式的傳回類型是 `void` (也就是說，函式宣告為永不傳回值)，則函式呼叫運算式也會具有 `void` 類型  (如需詳細資訊，請參閱[函式呼叫](../c-language/function-calls.md))。  
  
## <a name="see-also"></a>請參閱  
 [函式呼叫運算子：()](../cpp/function-call-operator-parens.md)