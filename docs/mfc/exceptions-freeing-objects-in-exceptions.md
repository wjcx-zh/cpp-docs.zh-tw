---
title: 例外狀況：釋放例外狀況中的物件
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371991"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>例外狀況：釋放例外狀況中的物件

本文介紹了發生異常時釋放物件的需要和方法。 主題包括：

- [在本地端處理異常](#_core_handling_the_exception_locally)

- [銷毀物件後引發異常](#_core_throwing_exceptions_after_destroying_objects)

框架或應用程式引發的異常會中斷正常程式流。 因此,密切跟蹤物件非常重要,這樣在引發異常時可以正確釋放它們。

有兩種主要方法可以執行此操作。

- 使用**try**和**catch**關鍵字在本地處理異常,然後使用一個語句銷毀所有物件。

- 在將異常扔到塊外部以便進一步處理之前,銷毀**catch**塊中的任何物件。

下面將這兩種方法作為以下問題範例的解決方案進行說明:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

如上所述,如果由`myPerson``SomeFunc`引發異常,將不會刪除。 執行直接跳轉到下一個外部異常處理程式,繞過正常的函數退出和刪除物件的代碼。 當異常離開函數時,指向物件的指標將超出範圍,只要程式正在運行,物件佔用的記憶體就永遠不會恢復。 這是內存洩漏;將使用記憶體診斷檢測到它。

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>本地處理異常

**try/catch**範例提供了一種防禦性程式設計方法,用於避免記憶體泄漏,並確保物件在發生異常時被銷毀。 例如,本文前面顯示的示例可以重寫如下:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

此新範例設置一個異常處理程式來捕獲異常並在本地處理它。 然後,它正常退出函數並銷毀物件。 此示例的重要方面是,使用**try/catch**塊建立了捕獲異常的上下文。 如果沒有本地異常幀,函數永遠不會知道已引發異常,並且沒有機會正常退出並銷毀物件。

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>銷毀物件後引發異常

處理異常的另一種方法是將它們傳遞到下一個外部異常處理上下文。 在**catch**塊中,可以對本地分配的物件進行一些清理,然後引發異常以進行進一步處理。

引發函數可能需要或不需要取消分配堆物件。 如果函數總是在在正常情況下返回之前解分配堆物件,則函數還應在引發異常之前取消分配堆物件。 另一方面,如果函數在正常情況下返回之前通常不重新分配物件,則必須根據情況決定是否應處理堆物件。

下面的範例展示如何清理本地配置的物件:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

異常機制自動取消分配幀物件;幀物件的析構函數也稱為。

如果調用可以引發異常的函數,則可以使用**try/catch**塊來確保捕獲異常並有機會銷毀已創建的任何物件。 特別是,請注意,許多 MFC 函數可能會引發異常。

有關詳細資訊,請參閱[異常:捕獲和刪除異常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
