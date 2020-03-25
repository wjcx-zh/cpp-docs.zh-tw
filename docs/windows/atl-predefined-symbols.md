---
title: ATL 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: e0661dbf3dd02bef5f5f056c5f09b39e33d17364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168547"
---
# <a name="atl-predefined-symbols"></a>ATL 預先定義的符號

這些符號定義于 ATL 標頭檔中，但支援標準 Windows 應用程式函式和動作。 這些符號主要用於對話方塊。

當您使用[對話方塊編輯器](../windows/dialog-editor.md)中的對話方塊和控制項時，這些符號會出現在與通用控制項相關聯的[屬性視窗](/visualstudio/ide/reference/properties-window)中。 比方說，如果您的對話方塊有 [**取消**] 按鈕，該命令就會與 [**屬性**] 視窗中的符號 IDCANCEL 相關聯。

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

## <a name="requirements"></a>需求

ATL

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)<br/>
[Win32 預先定義的符號](../windows/win32-predefined-symbols.md)<br/>
