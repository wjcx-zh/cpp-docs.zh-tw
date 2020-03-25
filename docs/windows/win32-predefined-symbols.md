---
title: Win32 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
ms.openlocfilehash: ae79b4c1a4021b32f631c694b376d2202b345415
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165921"
---
# <a name="win32-predefined-symbols"></a>Win32 預先定義的符號

這些符號會在 Win32 標頭檔中定義，並支援標準 Windows 應用程式函式和動作。 這些符號主要與一般 UI 元素搭配使用。 當您在資源編輯器中使用控制項時，這些符號會出現在與通用控制項相關聯的[屬性視窗](/visualstudio/ide/reference/properties-window)中。 比方說，如果您的工具列應該會顯示應用程式圖示，此圖示就會與 [**屬性**] 視窗中的符號 IDI_SMALL 相關聯。

|||
|-|-|
|IDABORT|ctrl對話方塊、中止按鈕|
|IDC_STATIC|ctrl對話方塊中的靜態文字|
|IDCANCEL|ctrl對話方塊、取消按鈕|
|IDD_ABOUTBOX|關於產品 對話方塊|
|IDI_PROJECTNAME|圖示目前專案圖示|
|IDI_SMALL|圖示目前專案小圖示|
|IDIGNORE|ctrl在對話方塊上搭配 [略過] 按鈕使用|
|IDM_ABOUT|（功能表項目）與說明搭配使用 。關於 。|
|IDM_EXIT|（功能表項目）與檔案搭配使用 。結束 。|
|IDNO|ctrl對話方塊、沒有按鈕|
|IDOK|ctrl對話方塊、[確定] 按鈕|
|IDRETRY|ctrl對話方塊，重試按鈕|
|IDS_APP_TITLE|字串目前的應用程式名稱|
|IDYES|ctrl對話方塊、[是] 按鈕|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)<br/>
[ATL 預先定義的符號](../windows/atl-predefined-symbols.md)<br/>
