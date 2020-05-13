---
title: 標準命令和視窗 ID
ms.date: 11/04/2016
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
ms.openlocfilehash: a7f9e37702c686e13379d4034be94949f92e5e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372949"
---
# <a name="standard-command-and-window-ids"></a>標準命令和視窗 ID

MFC 程式庫在 Afxres.h 中定義了數種標準命令和視窗 ID。 這些 IT 在資源編輯器和[類嚮導](mfc-class-wizard.md)中最常用於將消息映射到處理程式函數。 所有標準命令都有**ID_** 首碼。 例如,當您使用功能表編輯器時,通常將「檔案打開」功能表項綁定到標準ID_FILE_OPEN命令 ID。

對於大多數標準`CWinThread`命令,應用程式代碼不需要引用命令 ID,因為框架本身通過其主框架類`CWinApp``CView``CDocument`(、、、、 等) 中的消息映射處理命令。

除了標準命令指示指示外,還定義了許多其他標準指示,這些標準指示的前置碼為**AFX_ID**。 這些指示碼包括標準視窗 I(首碼**AFX_IDW_)、** 字串 I(首碼**AFX_IDS_**)和其他幾個類型。

程式師很少使用以**AFX_ID**首碼開頭的代號,但在重寫也引用**AFX_ID**的框架函數時,您可能需要參考這些指示。

此參考中沒有個別記錄的 ID。 您可以在技術說明[20、21](../../mfc/tn020-id-naming-and-numbering-conventions.md)和[22](../../mfc/tn022-standard-commands-implementation.md)中找到有關[21](../../mfc/tn021-command-and-message-routing.md)它們的更多資訊。

> [!NOTE]
> 標頭檔 Afxres.h 間接包含在 Afxwin.h 中。 您必須在應用程式的資源指令碼 (.rc) 檔中明確包含下列陳述式：

[!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
