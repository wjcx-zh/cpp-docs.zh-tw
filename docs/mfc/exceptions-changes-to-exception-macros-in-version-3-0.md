---
title: 例外狀況：3.0 版例外狀況巨集的變更
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 72b343641b0b43d408c5820ca2a2af1de94ce327
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225055"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>例外狀況：3.0 版例外狀況巨集的變更

這是一個先進的主題。

在 MFC 版本3.0 和更新版本中，例外狀況處理宏已變更為使用 c + + 例外狀況。 本文說明這些變更會如何影響使用宏之現有程式碼的行為。

本文章涵蓋下列主題：

- [例外狀況類型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)

- [重新擲回例外狀況](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>例外狀況類型和 CATCH 宏

在舊版的 MFC 中， **CATCH**宏會使用 MFC 執行時間類型資訊來判斷例外狀況的類型。例外狀況的型別是在 catch 網站上決定，換句話說， 不過，使用 c + + 例外狀況時，例外狀況的型別一律是由擲回之例外狀況物件的型別來決定。 這會造成不相容的情況，也就是擲回之物件的指標類型與擲回之物件的類型不同。

下列範例說明 MFC 3.0 版和更早版本之間這項差異的結果：

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此程式碼在版本3.0 中的行為不同，因為控制項一律會傳遞至具有相符例外狀況宣告的第一個 **`catch`** 區塊。 Throw 運算式的結果

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

會擲回為 `CException*` ，即使它被視為 `CCustomException` 。 MFC 版本2.5 和舊版中的**CATCH**宏會使用 `CObject::IsKindOf` ，在執行時間測試類型。 因為運算式

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

為 true，第一個 catch 區塊會捕捉例外狀況。 在3.0 版中，使用 c + + 例外狀況來執行許多例外狀況處理宏，第二個 catch 區塊符合擲回的 `CException` 。

這類程式碼很罕見。 當例外狀況物件傳遞至另一個接受泛型的函式時，通常會出現此情況 `CException*` ，並執行「預先擲回」處理，最後會擲回例外狀況。

若要解決這個問題，請將擲回運算式從函式移至呼叫程式碼，並在產生例外狀況時擲回編譯器已知的實際類型例外狀況。

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>重新擲回例外狀況

Catch 區塊無法擲回它所攔截到的相同例外狀況指標。

例如，此程式碼在舊版中是有效的，但在3.0 版中將會有非預期的結果：

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

在 catch 區塊中使用**THROW**會導致 `e` 刪除指標，因此外部 catch 網站會收到不正確指標。 請使用**THROW_LAST**來重新擲回 `e` 。

如需詳細資訊，請參閱[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
