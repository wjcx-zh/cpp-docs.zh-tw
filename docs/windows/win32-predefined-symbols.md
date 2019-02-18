---
title: Win32 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
ms.openlocfilehash: 2b282db2680b2459fdbece41d3c0e0d15f523e44
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320441"
---
# <a name="win32-predefined-symbols"></a>Win32 預先定義的符號

這些符號定義在 Win32 的標頭檔，並支援標準的 Windows 應用程式函數和動作。 常見的 UI 項目主要用於這些符號。 當您使用資源編輯器中的控制項時，這些符號會出現在[屬性 視窗](/visualstudio/ide/reference/properties-window)通用控制項相關聯。 比方說，如果您的工具列應該會顯示應用程式圖示，圖示會與相關聯的符號 IDI_SMALL 中**屬性視窗**。

|||
|-|-|
|IDABORT|控制：對話方塊 [中止] 按鈕|
|IDC_STATIC|控制：在對話方塊中的靜態文字|
|IDCANCEL|控制：對話方塊的 [取消] 按鈕|
|IDD_ABOUTBOX| 對話方塊中：在對話方塊中的相關產品|
|IDI_PROJECTNAME|圖示: 目前的專案圖示|
|IDI_SMALL|圖示: 目前專案的小圖示|
|IDIGNORE|控制：用於對話方塊中的 [忽略] 按鈕|
|IDM_ABOUT|功能表項目：說明搭配使用...關於...|
|IDM_EXIT|功能表項目：搭配檔案...結束...|
|IDNO|控制：對話方塊的 [無] 按鈕|
|IDOK|控制：對話方塊 [確定] 按鈕|
|IDRETRY|控制：對話方塊的重試按鈕|
|IDS_APP_TITLE|字串：目前的應用程式名稱|
|IDYES|控制：對話方塊的 [是] 按鈕|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)<br/>
[ATL 預先定義的符號](../windows/atl-predefined-symbols.md)<br/>