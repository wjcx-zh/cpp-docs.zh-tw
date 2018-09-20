---
title: 初始化及清除文件和檢視 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdc1efa9d2284a48e4f906a326efcd62dd6c61b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412947"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>初始化及清除文件和檢視

在文件和檢視之後，使用下列方針以進行初始化和清除：

- MFC 架構會初始化文件和檢視，您則初始化加入的任何資料。

- 架構會在關閉文件和檢視後進行清除，因此您必須取消配置您在那些文件和檢視之成員函式的堆積上所配置的任何記憶體。

> [!NOTE]
>  還記得，初始設定，針對整個應用程式的最佳辦法，在覆寫[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)類別成員函式`CWinApp`，並清除整個應用程式的最佳辦法，在覆寫`CWinApp`成員函式[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)。

文件 (及其框架視窗及檢視) 在 MDI 應用程式中的生命週期如下所示：

1. 在動態建立過程中，會呼叫文件建構函式。

1. 每個新文件，文件的[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)或是[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)呼叫。

1. 使用者在文件的整個存留期間與其互動。 通常，當使用者透過這個檢視使用文件資料、選取和編輯資料時，就會發生這種情況。 這個檢視會將變更傳遞到文件以供保存及更新其他檢視。 在這個時段，文件和檢視可能會處理命令。

1. 這個架構會呼叫[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)刪除文件特有的資料。

1. 會呼叫文件的解構函式。

在 SDI 應用程式中，當第一次建立文件時，會執行一次步驟 1。 然後，每次開啟新的文件時，重複執行步驟 2 至 4。 新文件會重複使用現有的資料物件。 最後，當應用程式結束時，執行第 5 步驟。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [初始化文件和檢視](../mfc/initializing-documents-and-views.md)

- [清除文件和檢視](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)

