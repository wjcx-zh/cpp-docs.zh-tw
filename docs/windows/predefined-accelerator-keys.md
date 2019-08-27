---
title: 快速鍵 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362383"
---
# <a name="accelerator-keys-c"></a>快速鍵 (C++)

## <a name="predefined-accelerator-keys"></a>預先定義的快速鍵

Windows 應用程式專案中可能包含許多預先定義的快速鍵。 其中有部分是用於 Windows 環境的虛擬按鍵。 其他支援的瀏覽器或 Unicode 應用程式。 您可以在任何加速器中使用任何此類按鍵。

|Key|描述|
|---------|-----------------|
|VK_ACCEPT|(IME) 接受|
|VK_BROWSER_BACK|(Windows)瀏覽器中，**回**金鑰|
|VK_BROWSER_FAVORITES|(Windows)瀏覽器中，**我的最愛**金鑰|
|VK_BROWSER_FORWARD|(Windows)瀏覽器中，**向前**金鑰|
|VK_BROWSER_HOME|(Windows)瀏覽器中，**開始**並**首頁**金鑰|
|VK_BROWSER_REFRESH|(Windows)瀏覽器中，**重新整理**金鑰|
|VK_BROWSER_SEARCH|(Windows)瀏覽器中，**搜尋**金鑰|
|VK_BROWSER_STOP|(Windows)瀏覽器中，**停止**金鑰|
|VK_CONVERT|(IME) 轉換|
|VK_FINAL|(IME) 最終模式|
|VK_HANGUEL|(IME)Hanguel 模式 （維護相容性，使用 VK_HANGUL）|
|VK_HANGUL|(IME)韓文模式|
|VK_HANJA|(IME)漢字模式|
|VK_JUNJA|(IME)Junja 模式|
|VK_KANA|(IME)Kana 模式|
|VK_KANJI|(IME)日文漢字模式|
|VK_LAUNCH_APP1|(Windows)**啟動應用程式 1**金鑰|
|VK_LAUNCH_APP2|(Windows)**啟動應用程式 2**金鑰|
|VK_LAUNCH_MAIL|(Windows)**啟動郵件**金鑰|
|VK_LAUNCH_MEDIA_SELECT|(Windows)**選取媒體**金鑰|
|VK_LCONTROL|**左 Ctrl**金鑰|
|VK_LMENU|**左 Menu**金鑰|
|VK_LSHIFT|**左 Shift**金鑰|
|VK_MEDIA_NEXT_TRACK|(Windows)**下一首**金鑰|
|VK_MEDIA_PLAY_PAUSE|(Windows)**矔菛/縸媒體**金鑰|
|VK_MEDIA_PREV_TRACK|(Windows)**上一首**金鑰|
|VK_MEDIA_STOP|(Windows)**停止媒體**金鑰|
|VK_MODECHANGE|(IME) 模式變更要求|
|VK_NONCONVERT|(IME) 非轉換|
|VK_OEM_1|(Windows)用於美國標準鍵盤 **;:** 金鑰|
|VK_OEM_102|(Windows)角括號索引鍵或 RT 102-key 鍵盤上的反斜線按鍵|
|VK_OEM_2|(Windows)用於美國標準鍵盤 **/？** key|
|VK_OEM_3|(Windows)用於美國標準鍵盤 **`~** 金鑰|
|VK_OEM_4|(Windows)用於美國標準鍵盤 **[{** 金鑰|
|VK_OEM_5|(Windows)用於美國標準鍵盤 **\\ &#124;** 金鑰|
|VK_OEM_6|(Windows)用於美國標準鍵盤 **]}** 金鑰|
|VK_OEM_7|(Windows)用於美國標準鍵盤 ' 單一-單引號/雙引號 」 按鍵|
|VK_OEM_COMMA|(Windows)任何國家/地區，如 **，** 金鑰|
|VK_OEM_MINUS|(Windows)任何國家/地區，如 **-** 金鑰|
|VK_OEM_PERIOD|(Windows)用於任何國家/地區， **。** key|
|VK_OEM_PLUS|(Windows)任何國家/地區，如 **+** 金鑰|
|VK_PACKET|(Windows)用來傳遞 Unicode 字元，如同它們是按鍵輸入。|
|VK_RCONTROL|**右 Ctrl**金鑰|
|VK_RMENU|**右 Menu**金鑰|
|VK_RSHIFT|**右 Shift**金鑰|
|VK_SLEEP|**電腦睡眠**金鑰|
|VK_VOLUME_DOWN|(Windows)**音量降低**金鑰|
|VK_VOLUME_MUTE|(Windows)**靜音**金鑰|
|VK_VOLUME_UP|(Windows)**音量提高**金鑰|
|VK_XBUTTON1|(Windows)**X1**滑鼠按鈕|
|VK_XBUTTON2|(Windows)**X2**滑鼠按鈕|

## <a name="accelerator-key-association"></a>快速鍵對應鍵的關聯

您經常想要功能表項目和鍵盤的組合，以發出相同的程式命令。 您可以執行此動作的功能表項目和您的應用程式快速鍵對應表中的項目，請指派相同的資源識別碼 (ID)。 然後，您會編輯功能表項目的標題，以顯示快速鍵的名稱。 如需有關的功能表項目和快速鍵的詳細資訊，請參閱[功能表命令](../windows/associating-a-menu-command-with-an-accelerator-key.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[快速鍵編輯器](../windows/accelerator-editor.md)<br/>