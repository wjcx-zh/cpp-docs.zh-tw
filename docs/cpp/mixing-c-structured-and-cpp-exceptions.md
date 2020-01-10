---
title: 混合 C （結構化） C++和例外狀況
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246453"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C （結構化） C++和例外狀況

如果您想要撰寫可移植的C++程式碼，則不建議在程式中使用結構化例外狀況處理（SEH）。 不過，您有時可能會想要使用[/eha](../build/reference/eh-exception-handling-model.md)和混合結構化例外C++狀況和原始程式碼進行編譯，而且需要一些功能來處理這兩種例外狀況。 由於結構化例外狀況處理常式沒有物件或具類型例外狀況的概念，因此無法處理C++程式碼擲回的例外狀況。 不過， C++ **catch**處理常式可以處理結構化例外狀況。 C++C 編譯器不接受例外狀況處理語法（**try**、 **throw**、 **catch**），但C++編譯器支援結構化例外狀況處理語法（ **__try**、 **__except**、 **__finally**）。

如 C++需如何將結構化例外狀況當做例外狀況處理的詳細資訊，請參閱 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md)。

如果您混用結構C++化和例外狀況，請注意下列潛在問題：

- C++ 例外狀況和結構化例外狀況無法在同一個函式中混用。

- 終止處理常式（ **__finally**區塊）一律會執行，即使在擲回例外狀況之後回溯期間也一樣。

- C++例外狀況處理可以在所有以[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項編譯的模組中攔截並保留回溯語義，這會啟用回溯語義。

- 在某些情況下，可能不會針對所有物件呼叫解構函式的函式。 例如，如果在嘗試透過未初始化的函式指標進行函式呼叫時發生結構化例外狀況，而且該函式採用在呼叫之前所建立的參數物件，則不會呼叫這些物件的析構函式堆疊回溯期間。

## <a name="next-steps"></a>接下來的步驟

- [在程式中C++使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)

  查看在程式中C++使用 `setjmp` 和 `longjmp` 的詳細資訊。

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

  請參閱您可以用C++來處理結構化例外狀況之方式的範例。

## <a name="see-also"></a>另請參閱

[例外C++狀況和錯誤處理的現代化最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)
