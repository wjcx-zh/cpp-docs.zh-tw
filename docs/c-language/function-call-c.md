---
title: "函式呼叫 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a86b3e45b5a5ce8c681fe267b7de8386b5fbc5c2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="function-call-c"></a>函式呼叫 (C)
「函式呼叫」是運算式，其中包含所呼叫函式的名稱，或函式指標的值，以及傳遞至函式的選擇性引數。  
  
## <a name="syntax"></a>語法  
 *postfix-expression*：  
 *postfix-expression*  **(**  *argument-expression-list* opt**)**  
  
 *argument-expression-list*：  
 *assignment-expression*  
  
 *argument-expression-list*  **,**  *assignment-expression*  
  
 *postfix-expression* 必須評估為函式位址 (例如，函式識別項或函式指標的值)，而 *argument-expression-list* 是運算式的清單 (以逗號分隔)，其中的值 (引數) 會傳遞至函式。 *argument-expression-list* 引數可以是空的。  
  
 函式呼叫運算式具有函式傳回值的值和類型。 函式不能傳回陣列類型的物件。 如果函式的傳回類型是 `void` (也就是說，函式宣告為永不傳回值)，則函式呼叫運算式也會具有 `void` 類型  (如需詳細資訊，請參閱[函式呼叫](../c-language/function-calls.md))。  
  
## <a name="see-also"></a>另請參閱  
 [函式呼叫運算子：()](../cpp/function-call-operator-parens.md)
