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
ms.openlocfilehash: 1b11bfe18443858de0dd7032f72fecadb1d6ebdd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626043"
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪貼簿：使用 Windows 剪貼簿

本主題說明如何在 MFC 應用程式中使用標準的 Windows 剪貼簿 API。

Windows 的大部分應用程式都支援將資料剪下或複製到 Windows 剪貼簿，並貼上剪貼簿中的資料。 剪貼簿資料格式會因應用程式而異。 針對有限數目的類別，此架構僅支援有限數目的剪貼簿格式。 您通常會在視圖的 [編輯] 功能表上，執行剪貼簿相關的命令（剪下、複製和貼上）。 類別庫會定義下列命令的命令識別碼： **ID_EDIT_CUT**、 **ID_EDIT_COPY**和**ID_EDIT_PASTE**。 其訊息行提示也會一併定義。

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)會說明如何藉由將功能表命令對應至處理常式函式，來處理應用程式中的功能表命令。 只要您的應用程式未在 [編輯] 功能表上定義 [剪貼簿] 命令的處理常式函式，它們就會保持停用狀態。 若要撰寫剪下和複製命令的處理常式函式，請在您的應用程式中執行選取專案。 若要撰寫 [貼上] 命令的處理常式函式，請查詢剪貼簿，以查看它是否包含應用程式可接受之格式的資料。 例如，若要啟用 [複製] 命令，您可以撰寫類似下列的處理常式：

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

剪下、複製和貼上命令只有在特定內容中才有意義。 只有在已選取某個專案時，才應該啟用 [剪下] 和 [複製] 命令，而且只有在剪貼簿中有專案時，才會進行 [貼入] 您可以定義更新處理常式函式來啟用或停用這些命令（視內容而定），藉此提供此行為。 如需詳細資訊，請參閱[如何更新使用者介面物件](how-to-update-user-interface-objects.md)。

MFC 程式庫提供剪貼簿支援，可讓您使用和類別來編輯文字 `CEdit` `CEditView` 。 OLE 類別也簡化了涉及 OLE 專案的剪貼簿作業。 如需有關 OLE 類別的詳細資訊，請參閱[剪貼簿：使用 OLE 剪貼簿機制](clipboard-using-the-ole-clipboard-mechanism.md)。

執行其他的 [編輯] 功能表命令，例如 [復原（**ID_EDIT_UNDO**）] 和 [重做（**ID_EDIT_REDO**）] 也會留給您。 如果您的應用程式不支援這些命令，您可以使用 Visual C++ 資源編輯器，輕鬆地將它們從資源檔中刪除。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [複製和貼上資料](clipboard-copying-and-pasting-data.md)

- [使用 OLE 剪貼簿機制](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>另請參閱

[剪貼簿](clipboard.md)
