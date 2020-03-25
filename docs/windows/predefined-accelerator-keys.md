---
title: 快速鍵（C++）
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: beb4e878138da3dc2905c86e18fedc658d7ceecf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215146"
---
# <a name="accelerator-keys-c"></a>快速鍵（C++）

## <a name="predefined-accelerator-keys"></a>預先定義的快速鍵

Windows 應用程式專案中可能包含許多預先定義的快速鍵。 其中有部分是用於 Windows 環境的虛擬按鍵。 其他支援瀏覽器或 Unicode 應用程式。 您可以在任何加速器中使用任何此類按鍵。

|Key|描述|
|---------|-----------------|
|VK_ACCEPT|（IME）接受|
|VK_BROWSER_BACK|時段瀏覽器，**上一頁**鍵|
|VK_BROWSER_FAVORITES|時段瀏覽器 **、我**的最愛金鑰|
|VK_BROWSER_FORWARD|時段瀏覽器，**轉寄**金鑰|
|VK_BROWSER_HOME|時段瀏覽器、**開始**和**首頁**金鑰|
|VK_BROWSER_REFRESH|時段瀏覽器 **，重新**整理金鑰|
|VK_BROWSER_SEARCH|時段瀏覽器，**搜尋**金鑰|
|VK_BROWSER_STOP|時段瀏覽器、**停止**鍵|
|VK_CONVERT|（IME）轉換|
|VK_FINAL|（IME）最終模式|
|VK_HANGUEL|行列Hanguel 模式（為了相容性而維護，請使用 VK_HANGUL）|
|VK_HANGUL|行列韓文模式|
|VK_HANJA|行列朝鮮文模式|
|VK_JUNJA|行列Junja 模式|
|VK_KANA|行列假名模式|
|VK_KANJI|行列漢字模式|
|VK_LAUNCH_APP1|時段**啟動應用程式 1**鍵|
|VK_LAUNCH_APP2|時段**啟動應用程式 2**金鑰|
|VK_LAUNCH_MAIL|時段**啟動郵件**金鑰|
|VK_LAUNCH_MEDIA_SELECT|時段**選取媒體**金鑰|
|VK_LCONTROL|**左 Ctrl**鍵|
|VK_LMENU|**左側功能表**鍵|
|VK_LSHIFT|**左 Shift**鍵|
|VK_MEDIA_NEXT_TRACK|時段**下一個追蹤**鍵|
|VK_MEDIA_PLAY_PAUSE|時段**播放/暫停媒體**金鑰|
|VK_MEDIA_PREV_TRACK|時段**上一個追蹤**鍵|
|VK_MEDIA_STOP|時段**停止媒體**按鍵|
|VK_MODECHANGE|（IME）模式變更要求|
|VK_NONCONVERT|（IME）非轉換|
|VK_OEM_1|時段若為美國標準鍵盤，則為 **：** 鍵|
|VK_OEM_102|時段RT 102 鍵鍵盤上的角括弧鍵或反斜線鍵|
|VK_OEM_2|時段針對美國標準鍵盤， **/？** 索引鍵|
|VK_OEM_3|時段針對美國標準鍵盤， **`~** 鍵|
|VK_OEM_4|時段針對美國標準鍵盤， **[{** 金鑰|
|VK_OEM_5|時段針對美國標準鍵盤， **\\&#124;** 鍵|
|VK_OEM_6|時段適用于美國標準鍵盤的 **]}** 鍵|
|VK_OEM_7|時段針對美國標準鍵盤，' 單引號/雙引號 ' 鍵|
|VK_OEM_COMMA|時段任何國家/地區、 **、** 金鑰|
|VK_OEM_MINUS|時段針對任何國家/地區， **-** 金鑰|
|VK_OEM_PERIOD|時段若為任何國家/地區，則為 **。** 索引鍵|
|VK_OEM_PLUS|時段針對任何國家/地區， **+** 金鑰|
|VK_PACKET|時段用來傳遞 Unicode 字元，就像是按鍵一樣。|
|VK_RCONTROL|**右 Ctrl**鍵|
|VK_RMENU|**右功能表**鍵|
|VK_RSHIFT|**右 Shift**鍵|
|VK_SLEEP|**電腦睡眠**鍵|
|VK_VOLUME_DOWN|時段**磁片區關閉**按鍵|
|VK_VOLUME_MUTE|時段**磁片區靜音**鍵|
|VK_VOLUME_UP|時段**音量增加**金鑰|
|VK_XBUTTON1|時段**X1**滑鼠按鍵|
|VK_XBUTTON2|時段**X2**滑鼠按鍵|

## <a name="accelerator-key-association"></a>快速鍵關聯

您經常想要功能表項目和鍵盤的組合，以發出相同的程式命令。 若要執行此動作，您可以將相同的資源識別碼（ID）指派給功能表項目，並將專案加入應用程式的快速鍵對應表中。 然後，您會編輯功能表項目的標題，以顯示快速鍵的名稱。 如需功能表項目和快速鍵的詳細資訊，請參閱[功能表命令](../windows/associating-a-menu-command-with-an-accelerator-key.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[快速鍵編輯器](../windows/accelerator-editor.md)<br/>
