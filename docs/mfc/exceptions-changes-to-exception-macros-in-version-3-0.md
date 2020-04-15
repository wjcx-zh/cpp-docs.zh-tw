---
title: 例外狀況：3.0 版例外狀況巨集的變更
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365499"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>例外狀況：3.0 版例外狀況巨集的變更

這是一個高級主題。

在 MFC 版本 3.0 及更高版本中,異常處理宏已更改為使用C++異常。 本文介紹這些更改如何影響使用宏的現有代碼的行為。

本文章涵蓋下列主題：

- [例外類型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)

- [重新引發異常](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>例外類型和 CATCH 宏

在早期版本的 MFC 中 **,CATCH**宏使用 MFC 運行時類型資訊來確定異常的類型;異常的類型在捕獲網站確定,換句話說。 但是,對於C++異常,異常的類型始終由引發的異常對象的類型在引發網站中確定。 在極少數情況下,指向引發物件的指標類型與引發物件的類型不同,這將導致不相容。

下面的範例說明了 MFC 版本 3.0 和早期版本之間的這種差異的後果:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

此代碼在版本 3.0 中的行為不同,因為控件始終通過匹配的異常聲明傳遞到第一個**catch**塊。 引發表示式的結果

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

被拋出為`CException*`,即使它建構為`CCustomException`。 MFC 版本 2.5 和更`CObject::IsKindOf`早版本的**CATCH**宏用於在運行時測試類型。 因為運算式

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

為 true,第一個 catch 塊捕獲異常。 在版本 3.0 中,使用C++個異常來實現許多異常處理宏,第二個 catch`CException`塊與引發的操作匹配 。

像這樣的代碼並不常見。 當異常物件傳遞給接受泛型`CException*`的另一個函數,執行"預引發"處理,最後引發異常時,通常會出現異常。

要解決此問題,請將 throw 表達式從函數移動到調用代碼,並引發編譯器在生成異常時已知的實際類型的異常。

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>重新引發異常

catch 塊無法引發捕獲的異常指標。

例如,此代碼在以前的版本中有效,但在版本 3.0 中會有意外的結果:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

在 catch 塊中使用**THROW**`e`會導致刪除指標,以便外部捕獲網站將接收無效的指標。 使用**THROW_LAST**重新`e`引發 。

有關詳細資訊,請參閱[異常:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
