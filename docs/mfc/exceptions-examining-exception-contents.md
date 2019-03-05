---
title: '例外狀況: 檢查例外狀況內容'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: f6f9bca6f6b7ca9d104cb492c760ab89f7163afd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259382"
---
# <a name="exceptions-examining-exception-contents"></a>例外狀況: 檢查例外狀況內容

雖然**攔截**區塊的引數可以是幾乎任何資料類型、 MFC 函式會擲回的例外狀況衍生自類別之型別的`CException`。 若要攔截 MFC 函式擲回例外狀況，接著，您撰寫**攔截**其引數為指標的區塊來`CException`物件 (或衍生自`CException`，例如`CMemoryException`)。 根據例外狀況的確切類型，您可以檢查例外狀況物件資料成員，收集的特定原因的例外狀況的資訊。

例如，`CFileException`型別具有`m_cause`資料成員，其中包含指定的檔案例外狀況原因的列舉型別。 可能的一些範例會傳回值為`CFileException::fileNotFound`和`CFileException::readOnly`。

下列範例示範如何檢查的內容`CFileException`。 同樣地可以檢查其他例外狀況類型。

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

如需詳細資訊，請參閱[例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)和[例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
