---
title: MSVC 中的例外處理
description: C++語言引用異常處理概述。
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396273"
---
# <a name="exception-handling-in-msvc"></a>MSVC 中的例外處理

例外狀況是可能超出程式控制範圍的錯誤條件，它會使得程式無法繼續沿著其正常執行路徑進行。 某些操作(包括物件創建、檔輸入/輸出和從其他模組進行的函數調用)都是異常的潛在來源,即使程式運行正確也是如此。 穩定的程式碼會預測及處理例外狀況。 要檢測邏輯錯誤,請使用斷言而不是異常(請參閱[使用斷言](/visualstudio/debugger/c-cpp-assertions))。

## <a name="kinds-of-exceptions"></a>例外類型

Microsoft C++編譯器 (MSVC) 支援三種異常處理:

- [C++異常處理](errors-and-exception-handling-modern-cpp.md)

   對於大多數C++程式,應使用C++異常處理。 它是類型安全的,並確保在堆疊展開期間調用物件析構函數。

- [結構化異常處理](structured-exception-handling-c-cpp.md)

   Windows 提供其自己的異常機制,稱為結構化異常處理 (SEH)。 不建議用於C++或 MFC 程式設計。 僅在非 MFC C 程式中使用 SEH。

- [MFC 例外狀況](../mfc/exception-handling-in-mfc.md)

   自版本 3.0 以來,MFC 一直使用C++異常。 它仍然支援其較舊的異常處理宏,這些宏類似於窗體中C++異常。 有關混合 MFC 宏和C++異常的建議,請參閱[例外:使用 MFC 宏和C++異常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

使用[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項指定要在C++專案中使用的異常處理模型。 標準C++異常處理 (**/EHsc**) 是 Visual Studio 中新C++專案中的預設值。

我們不建議您混合異常處理機制。 例如,不要使用C++異常進行結構化異常處理。 使用C++異常處理獨佔功能可使代碼更加便於使用,並且允許您處理任何類型的異常。 有關結構化異常處理的缺點的詳細資訊,請參閱[結構化異常處理](structured-exception-handling-c-cpp.md)。

## <a name="in-this-section"></a>本節內容

- [用於例外和錯誤處理的現代C++最佳實務](errors-and-exception-handling-modern-cpp.md)

- [如何設計異常安全](how-to-design-for-exception-safety.md)

- [如何連結例外狀況與非例外狀況代碼](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [try、catch 和 throw 陳述式](try-throw-and-catch-statements-cpp.md)

- [Catch 區塊的評估方式](how-catch-blocks-are-evaluated-cpp.md)

- [堆疊與堆疊](exceptions-and-stack-unwinding-in-cpp.md)

- [例外規格](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未處理的 C++ 例外狀況](unhandled-cpp-exceptions.md)

- [混合 C (結構化) 和 C++ 例外狀況](mixing-c-structured-and-cpp-exceptions.md)

- [結構化例外狀況處理 (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>另請參閱

[C++語言參考](cpp-language-reference.md)</br>
[x64 例外狀況處理](../build/exception-handling-x64.md)</br>
[例外處理(C++/CLI 和C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
