---
title: 使用文件
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: fb35d1731912b2e322bc61621f7900e0d98e1e72
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294664"
---
# <a name="using-documents"></a>使用文件

一同合作、 文件和檢視：

- 包含、 管理及顯示您的應用程式特有[資料](../mfc/managing-data-with-document-data-variables.md)。

- 提供介面組成[文件資料變數](../mfc/managing-data-with-document-data-variables.md)為了操作資料。

- 參與[寫入和讀取檔案](../mfc/serializing-data-to-and-from-files.md)。

- 參與[列印](../mfc/role-of-the-view-in-printing.md)。

- [處理](../mfc/handling-commands-in-the-document.md)大部分的應用程式的命令和訊息。

文件是特別專注於管理資料。 一般來說，儲存您的資料，在文件類別成員變數中。 檢視會使用這些變數來存取資料，以供顯示及更新。 讀取和寫入資料，從檔案，就會管理文件的預設序列化機制。 命令 （但不是 WM_COMMAND 以外的 Windows 訊息），也可以處理文件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [從 CDocument 衍生文件類別](../mfc/deriving-a-document-class-from-cdocument.md)

- [使用文件資料變數管理資料](../mfc/managing-data-with-document-data-variables.md)

- [從檔案序列化資料](../mfc/serializing-data-to-and-from-files.md)

- [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)

- [處理文件中的命令](../mfc/handling-commands-in-the-document.md)

- [OnNewDocument 成員函式](../mfc/reference/cdocument-class.md#onnewdocument)

- [DeleteContents 成員函式](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)
