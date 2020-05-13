---
title: 例外狀況：使用 MFC 巨集和 C++ 例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371596"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>例外狀況：使用 MFC 巨集和 C++ 例外狀況

本文討論了編寫同時使用 MFC 異常處理宏和C++異常處理關鍵字的代碼的注意事項。

本文章涵蓋下列主題：

- [混合例外關鍵字和巨集](#_core_mixing_exception_keywords_and_macros)

- [試著 catch 區塊的區塊](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>混合例外關鍵字和巨集

您可以在同一程式中混合 MFC 異常宏和C++異常關鍵字。 但是,您不能將 MFC 宏與同一塊中的C++異常關鍵字混合在一起,因為宏在異常物件超出範圍時會自動刪除它們,而使用異常處理關鍵字的代碼則不刪除它們。 有關詳細資訊,請參閱文章[「例外:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)」。

宏和關鍵字之間的主要區別是,宏"自動"刪除捕獲的異常,當異常超出範圍時。 使用關鍵字的代碼不;必須顯式刪除捕獲塊中捕獲的異常。 混合宏和C++異常關鍵字可能會導致未刪除異常物件時記憶體洩漏,或者在異常刪除兩次時導致堆損壞。

例如,以下代碼使異常指標無效:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

出現此問題的原因是`e`在執行從"內部 **"CATCH**塊中傳遞時被刪除。 使用**THROW_LAST**宏而不是**THROW**語句將導致「外部 **」CATCH**塊接收有效的指標:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>試著 Catch 區塊的區塊

不能從**CATCH**塊內**的嘗試**塊中重新引發當前異常。 以下範例不合法:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

有關詳細資訊,請參閱[異常:檢查異常內容](../mfc/exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
