---
title: 函式概觀
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
ms.openlocfilehash: 89c9f24b049ee8e9a33557f3262cd6abcc624957
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217060"
---
# <a name="overview-of-functions"></a>函式概觀

函式必須具有定義，而且應該具有宣告，不過，如果宣告在呼叫函式之前出現，則定義可以做為宣告。 函式定義包括函式主體，也就是呼叫函式時執行的程式碼。

函式宣告會為程式中其他位置定義的函式建立名稱、傳回類型和屬性。 函式宣告必須在函式呼叫之前。 這就是為什麼包含執行階段函式宣告的標頭檔會包括在您的程式碼中，並且位於執行階段函式呼叫之前。 如果宣告包含有關參數類型和數目的資訊，則宣告為原型。 如需詳細資訊，請參閱[函式原型](../c-language/function-prototypes.md)。

編譯器會使用原型比較後續函式呼叫中的引數類型與函式的參數，並且在必要時將引數類型轉換成參數的類型。

函式呼叫會將執行控制項從發出呼叫的函式傳遞至所呼叫的函式。 引數 (如果有的話) 會以傳值的方式傳遞至所呼叫的函式。 執行所呼叫函式中的語句會傳回 **`return`** 控制項，而且可能會傳回呼叫函式的值。

## <a name="see-also"></a>另請參閱

[函式](../c-language/functions-c.md)
