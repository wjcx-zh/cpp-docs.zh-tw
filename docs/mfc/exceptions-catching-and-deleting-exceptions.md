---
title: 例外狀況：攔截及刪除例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 5c1edd4c5d31d9a0e8e5270d074d25b5dd129a0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184243"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外狀況：攔截及刪除例外狀況

下列指示和範例示範如何攔截和刪除例外狀況。 如需 **`try`** 、和關鍵字的詳細資訊 **`catch`** **`throw`** ，請參閱[例外狀況和錯誤處理的新式 c + + 最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)。

您的例外狀況處理常式必須刪除其所處理的例外狀況物件，因為每當程式碼攔截例外狀況時，若無法刪除例外狀況就會導致記憶體流失。

您的 **`catch`** 區塊必須在下列情況中刪除例外狀況：

- 區塊會擲回 **`catch`** 新的例外狀況。

   當然，如果您再次擲回相同的例外狀況，則不得刪除例外狀況：

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 執行會從區塊內傳回 **`catch`** 。

> [!NOTE]
> 刪除時 `CException` ，請使用成員函式 `Delete` 來刪除例外狀況。 請勿使用 **`delete`** 關鍵字，因為如果例外狀況不在堆積上，它可能會失敗。

#### <a name="to-catch-and-delete-exceptions"></a>攔截和刪除例外狀況

1. 使用 **`try`** 關鍵字來設定 **`try`** 區塊。 執行可能會在區塊內擲回例外狀況的任何程式語句 **`try`** 。

   使用 **`catch`** 關鍵字來設定 **`catch`** 區塊。 將例外狀況處理常式代碼放在 **`catch`** 區塊中。 **`catch`** 只有當區塊內的程式碼擲回語句中所指定類型的例外狀況時，才會執行區塊中的 **`try`** 程式碼 **`catch`** 。

   下列基本架構會顯示 **`try`** **`catch`** 一般如何排列和區塊：

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   當擲回例外狀況時，控制權會傳遞給 **`catch`** 其例外狀況宣告符合例外狀況類型的第一個區塊。 您可以選擇性地使用連續區塊來處理不同類型的例外狀況， **`catch`** 如下所示：

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

如需詳細資訊，請參閱[例外狀況：從 MFC 例外狀況宏轉換](exceptions-converting-from-mfc-exception-macros.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
