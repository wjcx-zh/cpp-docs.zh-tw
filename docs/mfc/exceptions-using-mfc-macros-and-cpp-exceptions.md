---
title: '例外狀況: 使用 MFC 巨集和C++例外狀況'
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
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406011"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>例外狀況: 使用 MFC 巨集和C++例外狀況

本文將告訴您撰寫使用這兩個 MFC 例外狀況處理巨集的程式碼的考量，C++例外狀況處理關鍵字。

本文章涵蓋下列主題：

- [混用例外狀況關鍵字和巨集](#_core_mixing_exception_keywords_and_macros)

- [Try catch 區塊內的區塊](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> 混用例外狀況關鍵字和巨集

您可以混合使用 MFC 例外狀況巨集和C++的相同程式中的例外狀況關鍵字。 但您不能混用 MFC 巨集與C++相同的區塊中的例外狀況關鍵字因為巨集會刪除例外狀況物件，在超出範圍，而時，自動程式碼使用例外狀況處理關鍵字則否。 如需詳細資訊，請參閱文章[例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

巨集和關鍵字的主要差異是當例外狀況超出範圍時，巨集 「 自動 」 刪除已攔截的例外狀況。 使用這些關鍵字的程式碼則否;在 catch 區塊中攔截的例外狀況必須明確刪除。 混用巨集和C++例外狀況關鍵字可以不刪除例外狀況物件時，會導致記憶體流失，或兩次刪除例外狀況時，堆積損毀。

下列程式碼，比方說，會導致無效的例外狀況指標：

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

發生問題的原因`e`時執行會通過 「 內部 」 之外，會刪除**攔截**區塊。 使用**THROW_LAST**巨集，而不是**擲回**陳述式將會導致 「 外部 」**攔截**區塊來接收有效的指標：

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> Try Catch 區塊內的區塊

您無法從重新擲回目前例外狀況**嘗試**區塊內**攔截**區塊。 下列範例中是無效的：

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

如需詳細資訊，請參閱[例外狀況：檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
