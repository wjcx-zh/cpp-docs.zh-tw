---
title: 標準命令和視窗 ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: 40783bc19e51afb0e9fe9e4a429df0239a8e7f09
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907721"
---
# <a name="standard-command-and-window-ids"></a>標準命令和視窗 ID

MFC 程式庫在 Afxres.h 中定義了數種標準命令和視窗 ID。 這些識別碼最常用於資源編輯器和[類別嚮導](mfc-class-wizard.md)中，可將訊息對應至您的處理常式函式。 所有標準命令都具有**ID_** 前置詞。 例如，當您使用功能表編輯器時，通常會將 [開啟檔案] 功能表項目系結至標準 ID_FILE_OPEN 命令識別碼。

對於大部分的標準命令，應用程式代碼不需要參照命令 ID，因為架構本身會透過其主要架構類別`CWinThread`（、 `CWinApp`、 `CView` `CDocument`、和）中的訊息對應來處理命令。以此類推）。

除了標準的命令識別碼之外，還有一些其他的標準識別碼會定義，其前置詞為**AFX_ID**。 這些識別碼包含標準視窗識別碼（前置詞**AFX_IDW_** ）、字串 id （前置詞**AFX_IDS_** ）和數個其他類型。

程式設計人員很少使用以**AFX_ID**前置詞開頭的識別碼，但在覆寫同時參考**AFX_ID**的架構函式時，您可能需要參考這些識別碼。

此參考中沒有個別記錄的 ID。 您可以在技術提示[20](../../mfc/tn020-id-naming-and-numbering-conventions.md)、 [21](../../mfc/tn021-command-and-message-routing.md)和[22](../../mfc/tn022-standard-commands-implementation.md)中找到詳細資訊。

> [!NOTE]
>  標頭檔 Afxres.h 間接包含在 Afxwin.h 中。 您必須在應用程式的資源指令碼 (.rc) 檔中明確包含下列陳述式：

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
