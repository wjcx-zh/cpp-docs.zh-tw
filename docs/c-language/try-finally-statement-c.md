---
title: try-finally 陳述式 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: b800daa7689cef769ce3a3b070c957f18e8794c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213706"
---
# <a name="try-finally-statement-c"></a>try-finally 陳述式 (C)

**Microsoft 特定的**

`try-finally` 陳述式是 C 語言的 Microsoft 擴充功能，可讓應用程式在執行程式碼的區塊遭到中斷時，保證會執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 `try-finally` 陳述式對於有多個地方要檢查可能會導致常式過早傳回的錯誤時會特別有用。

*try-finally-statement*: **__try**  *compound-statement*

**`__finally`**  *複合陳述式*

`__try` 子句後面的複合陳述式是保護的區段。 子句後面的複合陳述式 **`__finally`** 是終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作、保護的區段是因例外狀況 (異常終止) 而結束，或依標準的執行順序 (正常終止) 而結束。

此時控制權會經由簡單的循序執行 (正常執行) 到達 `__try` 陳述式。 當控制權進入 `__try` 陳述式時，與它關聯的處理常式會變成作用中。 執行程序如下所示：

1. 執行保護的區段。

1. 已叫用終止處理常式。

1. 當終止處理常式完成時，執行會在 **`__finally`** 語句之後繼續。 無論保護區段如何結束（例如，透過來自 **`goto`** 受防護主體的語句，或透過 **`return`** 語句），終止處理常式都會在控制流程移出保護區段之前執行。

** `__leave** keyword is valid within a ` Try-finally ` statement block. The effect of **` __leave**是跳到區塊的結尾 `try-finally` 。 接著便會立即執行終止處理常式。 雖然 **`goto`** 可以使用語句來達到相同的結果，但是 **`goto`** 語句會導致堆疊回溯。 **' __Leave**語句更有效率，因為它不包含堆疊回溯。

`try-finally`使用 **`return`** 語句或執行時間函式結束語句會被 `longjmp` 視為異常終止。 雖然不可跳入 `__try` 陳述式，但是可以從這類陳述式跳出。 在 **`__finally`** 出發點和目的地之間使用的所有語句都必須執行。 這稱為「區域回溯」。

如果處理序在執行 `try-finally` 陳述式時被刪除，則不會呼叫終止處理常式。

> [!NOTE]
> 結構化例外狀況處理可搭配 C 和 C++ 原始程式檔使用。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理機制更有彈性，因為它可以處理任何類型的例外狀況。

> [!NOTE]
> 針對 C++ 程式，應該使用 C++ 例外狀況處理，而不是結構化例外狀況處理。 如需詳細資訊，請參閱《C++ 語言參考》** 中的[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。

查看 [try-except 陳述式](../c-language/try-except-statement-c.md)的範例以了解 `try-finally` 陳述式的運作方式。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[try-finally 語句](../cpp/try-finally-statement.md)
