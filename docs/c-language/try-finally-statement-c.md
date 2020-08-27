---
title: try-finally 陳述式 (C)
description: Microsoft C/c + + 會使用 try-catch 語句語言延伸模組，來實行 (SEH) 的結構化例外狀況處理。
ms.date: 08/24/2020
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 6f9cf901ed0a82b355880225c902ec4fc3e1082b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898703"
---
# <a name="try-finally-statement-c"></a>try-finally 陳述式 (C)

**Microsoft 特定**

`try-finally` 陳述式是 C 語言的 Microsoft 擴充功能，可讓應用程式在執行程式碼的區塊遭到中斷時，保證會執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 `try-finally` 陳述式對於有多個地方要檢查可能會導致常式過早傳回的錯誤時會特別有用。

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

子句後面的複合陳述式 **`__try`** 是受保護的區段。 子句後面的複合陳述式 **`__finally`** 是終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作。  (異常終止) 或依標準 (正常終止) 時，受保護的區段不會有任何影響。

藉 **`__try`** 由簡單的循序執行，將控制項傳遞至語句 (貫穿) 。 當控制項進入 **`__try`** 語句時，其相關聯的處理常式會變成作用中狀態。 執行程序如下所示：

1. 執行保護的區段。

1. 已叫用終止處理常式。

1. 終止處理常式完成時，會在語句之後繼續執行 **`__finally`** 。 無論受保護的區段如何結束 (例如，透過受防護 **`goto`** 主體以外的語句，或透過 **`return`** 語句) ，就會在控制流程移出保護區段之前執行終止處理常式。

**`__leave`** 關鍵字在語句區塊內是有效的 `try-finally` 。 的作用 **`__leave`** 是跳至 `try-finally` 區塊結尾。 接著便會立即執行終止處理常式。 雖然 **`goto`** 語句可以用來完成相同的結果，但是 **`goto`** 語句會導致堆疊回溯。 **`__leave`** 語句會更有效率，因為它不包含堆疊回溯。

`try-finally`使用 **`return`** 語句或 `longjmp` 執行時間函式結束語句會被視為異常終止。 跳入陳述並不合法 **`__try`** ，但要跳出一項。 您 **`__finally`** 必須執行在起飛點與目的地之間的所有使用中語句。 它稱為「 *本機*回溯」。

如果在執行語句時終止進程，則不會呼叫終止處理常式 `try-finally` 。

> [!NOTE]
> 結構化例外狀況處理可搭配 C 和 C++ 原始程式檔使用。 但是，它不是專為 c + + 所設計。 針對可移植的 c + + 程式，應該使用 c + + 例外狀況處理，而非結構化例外狀況處理。 此外，C++ 例外狀況處理機制更有彈性，因為它可以處理任何類型的例外狀況。 如需詳細資訊，請參閱*c + + 語言參考*中的[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

請參閱[ `try-except` 語句](../c-language/try-except-statement-c.md)的範例，查看 `try-finally` 語句的運作方式。

**結束 Microsoft 專用**

## <a name="see-also"></a>請參閱

[`try-finally` (c + +) 的語句 ](../cpp/try-finally-statement.md)
