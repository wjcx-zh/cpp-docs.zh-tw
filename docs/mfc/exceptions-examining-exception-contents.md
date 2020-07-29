---
title: 例外狀況：檢查例外狀況內容
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 7500db2a29f9d4ccef37b9265f5f2968c2d07993
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217944"
---
# <a name="exceptions-examining-exception-contents"></a>例外狀況：檢查例外狀況內容

雖然 **`catch`** 區塊的引數可以是幾乎任何資料類型，但 MFC 函式會擲回衍生自類別的類型例外狀況 `CException` 。 為了攔截 MFC 函式所擲回的例外狀況，您可以撰寫一個 **`catch`** 區塊，其引數是 `CException` 物件（或衍生自的物件 `CException` ，例如）的指標 `CMemoryException` 。 根據例外狀況的確切類型，您可以檢查例外狀況物件的資料成員，以收集例外狀況的特定原因的相關資訊。

例如， `CFileException` 類型具有 `m_cause` 資料成員，其中包含指定檔案例外狀況原因的列舉類型。 可能的傳回值的一些範例為 `CFileException::fileNotFound` 和 `CFileException::readOnly` 。

下列範例顯示如何檢查的內容 `CFileException` 。 其他的例外狀況類型也可以類似的檢查。

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

如需詳細資訊，請參閱[例外狀況：釋放例外狀況中的物件](exceptions-freeing-objects-in-exceptions.md)和[例外狀況：攔截及刪除例外](exceptions-catching-and-deleting-exceptions.md)狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
