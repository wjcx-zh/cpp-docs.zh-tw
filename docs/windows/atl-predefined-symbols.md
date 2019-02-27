---
title: ATL 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: 16991746c5c858310466f7eebd91a8478d2dcc5c
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954844"
---
# <a name="atl-predefined-symbols"></a>ATL 預先定義的符號

ATL 標頭檔中定義這些符號，但是它們可以支援標準的 Windows 應用程式函數和動作。 這些符號主要用於與對話方塊。

當您正在使用對話方塊和控制項中[對話方塊編輯器](../windows/dialog-editor.md)，這些符號會出現在**屬性**通用控制項相關聯的視窗。 比方說，如果您的對話方塊中有**取消**按鈕，命令將會是相關聯的符號 IDCANCEL 中[屬性 視窗](/visualstudio/ide/reference/properties-window)。

|||
|-|-|
|IDABORT|（控制項）對話方塊中，[中止] 按鈕|
|IDC_STATIC|（控制項）靜態控制項|
|IDCANCEL|（控制項）對話方塊中，[取消] 按鈕|
|IDIGNORE|（控制項）對話方塊中，[忽略] 按鈕|
|IDNO|（控制項）對話方塊中，沒有 按鈕|
|IDOK|（控制項）對話方塊中，[確定] 按鈕|
|IDR_ACCELERATOR1|（資源）快速鍵對應表|
|IDRETRY|（控制項）對話方塊中，重試按鈕|
|IDS_PROJNAME|（字串）目前的應用程式名稱|
|IDYES|（控制項）對話方塊中，[是] 按鈕|

## <a name="requirements"></a>需求

ATL

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)<br/>
[Win32 預先定義的符號](../windows/win32-predefined-symbols.md)<br/>