---
title: 函式呼叫 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 23531f25128fc267caa3a3cad5f2c52e603a2cc6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229684"
---
# <a name="function-call-c"></a>函式呼叫 (C)

「函式呼叫」** 是運算式，其中包含所呼叫函式的名稱，或函式指標的值，以及傳遞至函式的選擇性引數。

## <a name="syntax"></a>語法

後置*運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***（***引數運算式清單*<sub>opt</sub> **）**    

*argument-expression-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指派-運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*引數-運算式-清單* **，** *指派運算式*

*postfix-expression* 必須評估為函式位址 (例如，函式識別項或函式指標的值)，而 *argument-expression-list* 是運算式的清單 (以逗號分隔)，其中的值 (引數) 會傳遞至函式。 *argument-expression-list* 引數可以是空的。

函式呼叫運算式具有函式傳回值的值和類型。 函式不能傳回陣列類型的物件。 如果函式的傳回型 **`void`** 別是（也就是已宣告為「永不」傳回值），則函式呼叫運算式也會有 **`void`** 類型。 (如需詳細資訊，請參閱[函式呼叫](../c-language/function-calls.md))。

## <a name="see-also"></a>另請參閱

[函式呼叫運算子：（）](../cpp/function-call-operator-parens.md)
