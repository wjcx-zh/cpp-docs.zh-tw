---
title: 混用 C (結構化) 和 c + + 例外狀況
description: 如何混合結構化例外狀況處理和 c + + 例外狀況，以及一些潛在問題。
ms.date: 08/24/2020
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: 98ce2335ff3b08b7a5d71e03305c481ba068e5e6
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898407"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混用 C (結構化) 和 c + + 例外狀況

如果您想要撰寫可移植的程式碼，則不建議在 c + + 程式中使用結構化例外狀況處理 (SEH) 。 不過，您有時可能會想要使用 [`/EHa`](../build/reference/eh-exception-handling-model.md) 和混合結構化例外狀況和 c + + 原始程式碼，而且需要一些可處理這兩種例外狀況的功能。 因為結構化例外狀況處理常式沒有物件或具類型例外狀況的概念，所以無法處理 c + + 程式碼所擲回的例外狀況。 不過，c + + **`catch`** 處理常式可以處理結構化例外狀況。 C + + 例外狀況處理語法 (**`try`** 、 **`throw`** 、 **`catch`**) 不會被 c 編譯器接受，但結構化例外狀況處理語法 (**`__try`** ， **`__except`** **`__finally`**) 是由 c + + 編譯器支援。

[`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md)如需如何將結構化例外狀況處理為 c + + 例外狀況的資訊，請參閱。

如果您混用結構化和 c + + 例外狀況，請注意下列潛在問題：

- C + + 例外狀況和結構化例外狀況無法在相同的函式中混合。

- **`__finally`** 即使在擲回例外狀況之後回溯期間，一律會執行終止處理常式 (區塊) 。

- C + + 例外狀況處理可以在所有以編譯器選項編譯的模組中攔截並保留回溯語義 [`/EH`](../build/reference/eh-exception-handling-model.md) ，以啟用回溯語義。

- 在某些情況下，不會針對所有物件呼叫函式函數。 例如，嘗試透過未初始化的函式指標進行函式呼叫時，可能會發生結構化例外狀況。 如果函式參數是在呼叫之前所建立的物件，就不會在堆疊回溯期間呼叫這些物件的析構函式。

## <a name="next-steps"></a>後續步驟

- [`setjmp` `longjmp` 在 c + + 程式中使用或](../cpp/using-setjmp-longjmp.md)

  請參閱 `setjmp` `longjmp` c + + 程式中有關使用和的詳細資訊。

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

  請參閱您可以使用 c + + 處理結構化例外狀況的方法範例。

## <a name="see-also"></a>請參閱

[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)
