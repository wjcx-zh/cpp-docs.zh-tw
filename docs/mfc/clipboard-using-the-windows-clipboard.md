---
title: 剪貼簿：使用 Windows 剪貼簿
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 49111e4efd2a12264d61030fe038d80b974514c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326985"
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪貼簿：使用 Windows 剪貼簿

本主題描述如何使用標準的 Windows 剪貼簿 API，在 MFC 應用程式內。

大部分的應用程式的 Windows 支援剪下或將資料複製到 Windows 剪貼簿並貼上剪貼簿的資料。 剪貼簿資料格式是根據應用程式而異。 架構支援有限數目的類別只在有限的剪貼簿格式。 您通常會實作的剪貼簿相關的命令 — 剪下、 複製和貼上，檢視 [編輯] 功能表上。 Class library 會定義這些命令的命令識別碼：**ID_EDIT_CUT**， **ID_EDIT_COPY**，以及**ID_EDIT_PASTE**。 此外，也會定義其訊息列提示。

[訊息和架構中的命令](../mfc/messages-and-commands-in-the-framework.md)說明如何將功能表命令對應至處理常式函式中處理您的應用程式中的功能表命令。 只要您的應用程式不會在 [編輯] 功能表上定義的剪貼簿命令處理常式函式，它們會維持停用。 若要撰寫的剪下和複製命令的處理常式函式，實作應用程式中的選取項目。 若要撰寫貼上] 命令的處理常式函式，查詢 [剪貼簿，以查看它是否包含在您的應用程式可接受的格式中的資料。 例如，若要啟用 [複製] 命令，您可能會撰寫處理常式像下面這樣：

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

剪下、 複製和貼上命令只會在特定內容中有意義的。 只有在選取項目，並貼上 命令時，才項目是在剪貼簿時，應該啟用剪下和複製命令。 您可以提供這種行為來定義更新處理常式函式啟用或停用這些命令，視內容而定。 如需詳細資訊，請參閱 <<c0> [ 如何更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)。

Microsoft Foundation 類別庫提供文字編輯使用剪貼簿支援`CEdit`和`CEditView`類別。 OLE 類別也會簡化實作的剪貼簿作業涉及 OLE 項目。 如需有關 OLE 類別的詳細資訊，請參閱[剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。

實作其他編輯功能表命令，例如復原 (**ID_EDIT_UNDO**) 和取消復原 (**ID_EDIT_REDO**)，也會保留給您。 如果您的應用程式不支援這些命令，您可以輕鬆地刪除它們從您使用視覺效果的資源檔C++資源編輯器。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md)

- [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>另請參閱

[剪貼簿](../mfc/clipboard.md)
