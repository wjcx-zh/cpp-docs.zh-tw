---
title: 初始化及清除文件和檢視
ms.date: 11/04/2016
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
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626359"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>初始化及清除文件和檢視

在文件和檢視之後，使用下列方針以進行初始化和清除：

- MFC 架構會初始化文件和檢視，您則初始化加入的任何資料。

- 架構會在關閉文件和檢視後進行清除，因此您必須取消配置您在那些文件和檢視之成員函式的堆積上所配置的任何記憶體。

> [!NOTE]
> 回想一下，整個應用程式的初始化最好是在類別的[InitInstance](reference/cwinapp-class.md#initinstance)成員函式的覆寫中完成 `CWinApp` ，而整個應用程式的清除作業最好是在您的成員函式 ExitInstance 的覆寫中完成 `CWinApp` 。 [ExitInstance](reference/cwinapp-class.md#exitinstance)

文件 (及其框架視窗及檢視) 在 MDI 應用程式中的生命週期如下所示：

1. 在動態建立過程中，會呼叫文件建構函式。

1. 針對每個新檔，會呼叫檔的[OnNewDocument](reference/cdocument-class.md#onnewdocument)或[OnOpenDocument](reference/cdocument-class.md#onopendocument) 。

1. 使用者在文件的整個存留期間與其互動。 通常，當使用者透過這個檢視使用文件資料、選取和編輯資料時，就會發生這種情況。 這個檢視會將變更傳遞到文件以供保存及更新其他檢視。 在這個時段，文件和檢視可能會處理命令。

1. 架構會呼叫[DeleteContents](reference/cdocument-class.md#deletecontents)來刪除檔特定的資料。

1. 會呼叫文件的解構函式。

在 SDI 應用程式中，當第一次建立文件時，會執行一次步驟 1。 然後，每次開啟新的文件時，重複執行步驟 2 至 4。 新文件會重複使用現有的資料物件。 最後，當應用程式結束時，執行第 5 步驟。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [初始化文件和檢視](initializing-documents-and-views.md)

- [清除文件和檢視](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>另請參閱

[檔/視圖架構](document-view-architecture.md)
