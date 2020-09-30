---
title: " (c + +) 的快速鍵"
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 4f838caa8ca9e4a996fa4cb8018d663c6c7aecea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504297"
---
# <a name="accelerator-keys-c"></a> (c + +) 的快速鍵

## <a name="predefined-accelerator-keys"></a>預先定義的快速鍵

Windows 應用程式專案中可能包含許多預先定義的快速鍵。 其中有部分是用於 Windows 環境的虛擬按鍵。 其他支援瀏覽器或 Unicode 應用程式。 您可以在任何加速器中使用任何此類按鍵。

|Key|描述|
|---------|-----------------|
|VK_ACCEPT| (IME) 接受|
|VK_BROWSER_BACK| (Windows) 瀏覽器， **上一頁** 金鑰|
|VK_BROWSER_FAVORITES| (Windows) 瀏覽器 **，我** 的最愛金鑰|
|VK_BROWSER_FORWARD| (Windows) 瀏覽器、 **轉寄** 金鑰|
|VK_BROWSER_HOME| (Windows) 瀏覽器、 **開始** 和 **首頁** 金鑰|
|VK_BROWSER_REFRESH| (Windows) 瀏覽器 **，重新** 整理金鑰|
|VK_BROWSER_SEARCH| (Windows) 瀏覽器、 **搜尋** 金鑰|
|VK_BROWSER_STOP| (Windows) Browser， **Stop** key|
|VK_CONVERT| (IME) 轉換|
|VK_FINAL| (IME) 最終模式|
|VK_HANGUEL| (IME) Hanguel 模式 (針對相容性進行維護，請使用 VK_HANGUL) |
|VK_HANGUL| (IME) 韓文模式|
|VK_HANJA| (輸入法) 的漢字模式|
|VK_JUNJA| (IME) Junja 模式|
|VK_KANA| (IME) 假名模式|
|VK_KANJI| (IME) 漢字模式|
|VK_LAUNCH_APP1| (Windows) **啟動應用程式 1** 金鑰|
|VK_LAUNCH_APP2| (Windows) **啟動應用程式 2** 鍵|
|VK_LAUNCH_MAIL| (Windows) **開始郵件** 金鑰|
|VK_LAUNCH_MEDIA_SELECT| (Windows) **選取媒體** 金鑰|
|VK_LCONTROL|**左 Ctrl** 鍵|
|VK_LMENU|**左側功能表** 鍵|
|VK_LSHIFT|**左 Shift** 鍵|
|VK_MEDIA_NEXT_TRACK| (Windows) **Next Track** 鍵|
|VK_MEDIA_PLAY_PAUSE| (Windows) **播放/暫停媒體** 金鑰|
|VK_MEDIA_PREV_TRACK| (Windows) **上一個追蹤** 鍵|
|VK_MEDIA_STOP| (Windows) **停止媒體** 金鑰|
|VK_MODECHANGE| (IME) 模式變更要求|
|VK_NONCONVERT| (IME) nonconvert|
|VK_OEM_1|適用于 US 標準鍵盤的 Windows)  (**;：** key|
|VK_OEM_102| (Windows) RT 102-按鍵鍵盤上的角括弧鍵或反斜線鍵|
|VK_OEM_2| (Windows) 適用于 US 標準鍵盤的 **/？** 索引鍵|
|VK_OEM_3|適用于 US 標準鍵盤的 (Windows) ， **`~** 金鑰|
|VK_OEM_4|適用于 US 標準鍵盤的 (Windows) ， **[{** key]|
|VK_OEM_5| (Windows) 適用于 US 標準鍵盤， ** \\&#124;** 鍵|
|VK_OEM_6|適用于 US 標準鍵盤的 Windows)  (**]}** 鍵|
|VK_OEM_7|適用于 US 標準鍵盤的 (Windows) ，也就是「單引號/雙引號」索引鍵|
|VK_OEM_COMMA| (任何國家/地區的 Windows) ， **，** 金鑰|
|VK_OEM_MINUS| (任何國家/地區的 Windows) ， **-** 金鑰|
|VK_OEM_PERIOD| (任何國家/地區的 Windows) ，則為 **。** 索引鍵|
|VK_OEM_PLUS| (任何國家/地區的 Windows) ， **+** 金鑰|
|VK_PACKET| (Windows) 用來傳遞 Unicode 字元，就像是按鍵一樣。|
|VK_RCONTROL|**右 Ctrl** 鍵|
|VK_RMENU|**右鍵功能表** 鍵|
|VK_RSHIFT|**右 Shift** 鍵|
|VK_SLEEP|**電腦睡眠** 金鑰|
|VK_VOLUME_DOWN| (Windows) **音量降低** 金鑰|
|VK_VOLUME_MUTE| (Windows) **音量靜音** 按鍵|
|VK_VOLUME_UP| (Windows) **Volume Up** 鍵|
|VK_XBUTTON1| (Windows) **X1** 滑鼠按鍵|
|VK_XBUTTON2| (Windows) **X2** 滑鼠按鍵|

## <a name="accelerator-key-association"></a>快速鍵關聯

您經常想要功能表項目和鍵盤的組合，以發出相同的程式命令。 若要執行此動作，您可以將相同的資源識別碼 (識別碼) 指派給功能表項目，以及應用程式的快速鍵對應表中的專案。 然後，您會編輯功能表項目的標題，以顯示快速鍵的名稱。 如需功能表項目和快速鍵的詳細資訊，請參閱 [功能表命令](./menu-command-properties.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[快速鍵編輯器](../windows/accelerator-editor.md)<br/>
