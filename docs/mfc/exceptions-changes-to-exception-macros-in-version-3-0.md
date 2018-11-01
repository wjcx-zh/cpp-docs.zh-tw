---
title: 例外狀況：3.0 版例外狀況巨集的變更
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 54826ee7a7ac129ae69715b45770a0a66596a2a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607983"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>例外狀況：3.0 版例外狀況巨集的變更

這是進階的主題。

在 MFC 3.0 版和更新版本中，已變更的例外狀況處理巨集使用 c + + 例外狀況。 本文會說明這些變更如何影響使用巨集的現有程式碼的行為。

本文章涵蓋下列主題：

- [例外狀況類型和 CATCH 巨集](#_core_exception_types_and_the_catch_macro)

- [重新擲回例外狀況](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> 例外狀況類型和 CATCH 巨集

在舊版的 MFC**攔截**巨集使用 MFC 執行階段類型資訊來判斷例外狀況的類型，例外狀況的類型決定，也就是說，時，接收站台。 使用 c + + 例外狀況，不過，例外狀況的類型是一律取決於擲回站台就會擲回的例外狀況物件的類型。 在少數情況下擲回的物件指標的類型與擲回的物件類型不同，這會導致不相容。

下列範例說明這 MFC 3.0 版和更早版本之間的差異的結果：

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此程式碼的行為不同 3.0 版因為控制權一律會傳遞給第一個**攔截**與相符的例外狀況宣告的區塊。 Throw 運算式的結果

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

做為擲回`CException*`，即使它建構為`CCustomException`。 **攔截**MFC 版本 2.5 和更早版本使用的巨集`CObject::IsKindOf`測試在執行階段的類型。 因為運算式

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

為 true，第一個 catch 區塊攔截例外狀況。 在 3.0 版，您可以使用 c + + 例外狀況來實作許多例外狀況處理巨集，第二個 catch 區塊符合擲回`CException`。

就像這樣的程式碼並不常見。 它通常會出現 例外狀況物件傳遞至另一個函式可接受泛型`CException*`執行 「 前擲回 」 處理，且最後會擲回例外狀況。

若要解決此問題，將從函式的 throw 運算式移至呼叫端程式碼，並擲回例外狀況的編譯器會產生例外狀況時已知的實際型別。

##  <a name="_core_re.2d.throwing_exceptions"></a> 重新擲回例外狀況

在 catch 區塊不能擲回它攔截到的相同例外狀況指標。

比方說，此程式碼之前在舊版中中, 有效，但是會有非預期的結果，3.0 版：

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

使用**擲回**在 catch 區塊會導致指標`e`要刪除，以便在外部 catch 站台將會收到無效的指標。 使用**THROW_LAST**重新擲回`e`。

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)

