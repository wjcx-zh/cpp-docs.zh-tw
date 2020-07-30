---
title: 使用 setjmp 和 longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 6adbe22eb684c9a1dda080f6d35a99c55d6c3d30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226993"
---
# <a name="using-setjmp-and-longjmp"></a>使用 setjmp 和 longjmp

當使用[setjmp](../c-runtime-library/reference/setjmp.md)和[longjmp](../c-runtime-library/reference/longjmp.md)時，它們會提供執行非本機的方式 **`goto`** 。 它們通常用於 C 程式碼，以將執行控制傳遞給先前呼叫之常式中的錯誤處理或復原程式碼，而不需要使用標準的呼叫或傳回慣例。

> [!CAUTION]
> 因為 `setjmp` 和 `longjmp` 不支援正確地銷毀在 c + + 編譯器之間可能的堆疊框架物件，而且因為它可能會因為無法優化本機變數而降低效能，所以不建議在 c + + 程式中使用它們。 我們建議您 **`try`** 改用和 **`catch`** 結構。

如果您決定 `setjmp` `longjmp` 在 c + + 程式中使用和，也請包含 \<setjmp.h> 或，以確保函式 \<setjmpex.h> 與結構化例外狀況處理（SEH）或 c + + 例外狀況處理之間的正確互動。

**Microsoft 特定的**

如果您使用[/EH](../build/reference/eh-exception-handling-model.md)選項來編譯 c + + 程式碼，則會在堆疊回溯期間呼叫本機物件的析構函數。 不過，如果您使用 **/ehs**或 **/ehsc**進行編譯，而您的其中一個函式使用[noexcept](../cpp/noexcept-cpp.md)呼叫，則視優化工具的狀態而定，該 `longjmp` 函數的析構函數回溯可能不會發生。

在可移植的程式碼中， `longjmp` 執行呼叫時，標準會明確不保證以框架為基礎之物件的正確銷毀，而且其他編譯器可能不會支援。 為了讓您知道，在警告層級4，對的呼叫 `setjmp` 會導致警告 C4611： ' _setjmp ' 與 c + + 物件銷毀之間的互動是不可移植的。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[混合 C （結構化）和 c + + 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)
