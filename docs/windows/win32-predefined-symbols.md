---
title: Win32 預先定義的符號
ms.date: 02/14/2019
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
ms.openlocfilehash: f69dddcb8b6a9a390f80ab4d0112e19c4e8d32e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835645"
---
# <a name="win32-predefined-symbols"></a>Win32 預先定義的符號

這些符號是在 Win32 標頭檔中定義，而且它們支援標準 Windows 應用程式函式和動作。 這些符號主要用於通用的 UI 元素。 當您在資源編輯器中使用控制項時，這些符號會出現在與通用控制項相關聯的 [屬性視窗](/visualstudio/ide/reference/properties-window) 中。 比方說，如果您的工具列應該會顯示應用程式圖示，圖示就會與 [ **屬性** ] 視窗中的符號 IDI_SMALL 相關聯。

|名稱|描述|
|-|-|
|IDABORT| (控制項) 對話方塊、中止按鈕|
|IDC_STATIC| (控制項) 對話方塊中的靜態文字|
|IDCANCEL| (控制項) 對話方塊、[取消] 按鈕|
|IDD_ABOUTBOX|對話方塊) 產品的 (對話方塊|
|IDI_PROJECTNAME| (圖示) 目前的專案圖示|
|IDI_SMALL| (圖示) 目前專案小圖示|
|IDIGNORE| (控制項) 與對話方塊上的 [忽略] 按鈕搭配使用|
|IDM_ABOUT| (功能表項目) 與 [說明] 搭配使用 .。。關於 .。。|
|IDM_EXIT| (功能表項目) 與檔案搭配使用 .。。退出。。。|
|IDNO| (控制項) 對話方塊、沒有按鈕|
|IDOK| (控制項) 對話方塊、[確定] 按鈕|
|IDRETRY| (控制項) 對話方塊、重試按鈕|
|IDS_APP_TITLE| (字串) 目前的應用程式名稱|
|IDYES| (控制項) 對話方塊、是按鈕|

## <a name="requirements"></a>規格需求

Win32

## <a name="see-also"></a>另請參閱

[預先定義的符號 Id](../windows/predefined-symbol-ids.md)<br/>
[MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)<br/>
[ATL 預先定義的符號](../windows/atl-predefined-symbols.md)<br/>
