---
title: ATL 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: 4ce2d8060c7218226340a591c6295a573f99dad8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619773"
---
# <a name="atl-predefined-symbols"></a>ATL 預先定義的符號

這些符號定義于 ATL 標頭檔中，但支援標準 Windows 應用程式函式和動作。 這些符號主要用於對話方塊。

當您使用[對話方塊編輯器](dialog-editor.md)中的對話方塊和控制項時，這些符號會出現在與通用控制項相關聯的[屬性視窗](/visualstudio/ide/reference/properties-window)中。 比方說，如果您的對話方塊有 [**取消**] 按鈕，該命令就會與 [**屬性**] 視窗中的符號 IDCANCEL 相關聯。

|||
|-|-|
|IDABORT|ctrl對話方塊、中止按鈕|
|IDC_STATIC|ctrl靜態控制項|
|IDCANCEL|ctrl對話方塊、取消按鈕|
|IDIGNORE|ctrl對話方塊，忽略按鈕|
|IDNO|ctrl對話方塊、沒有按鈕|
|IDOK|ctrl對話方塊、[確定] 按鈕|
|IDR_ACCELERATOR1|resource快速鍵對應表|
|IDRETRY|ctrl對話方塊，重試按鈕|
|IDS_PROJNAME|字串目前的應用程式名稱|
|IDYES|ctrl對話方塊、[是] 按鈕|

## <a name="requirements"></a>規格需求

ATL

## <a name="see-also"></a>另請參閱

[預先定義的符號 Id](predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](mfc-predefined-symbols.md)<br/>
[Win32 預先定義的符號](win32-predefined-symbols.md)<br/>
