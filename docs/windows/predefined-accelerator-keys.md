---
title: 快速鍵 （c + +）
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
ms.openlocfilehash: 6ef8f84564d6fd1957452971cb1e88dc99aa27e9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320506"
---
# <a name="accelerator-keys-c"></a>快速鍵 （c + +）

## <a name="predefined-accelerator-keys"></a>預先定義的快速鍵

Windows 應用程式專案中可能包含許多預先定義的快速鍵。 其中有部分是用於 Windows 環境的虛擬按鍵。 其他則支援瀏覽器或 Unicode 應用程式。 您可以在任何加速器中使用任何此類按鍵。

|Key|描述|
|---------|-----------------|
|VK_ACCEPT|IME accept|
|VK_BROWSER_BACK|Windows：瀏覽器上一頁按鍵|
|VK_BROWSER_FAVORITES|Windows：瀏覽器我的最愛鍵|
|VK_BROWSER_FORWARD|Windows：瀏覽器下一頁按鍵|
|VK_BROWSER_HOME|Windows：瀏覽器啟動和首頁按鍵|
|VK_BROWSER_REFRESH|Windows：瀏覽器重新整理鍵|
|VK_BROWSER_SEARCH|Windows：瀏覽器搜尋鍵|
|VK_BROWSER_STOP|Windows：瀏覽器停止鍵|
|VK_CONVERT|輸入法轉換|
|VK_FINAL|輸入法最終模式|
|VK_HANGUEL|輸入法 Hanguel 模式 (維護相容性；使用 VK_HANGUL)|
|VK_HANGUL|輸入法韓文模式|
|VK_HANJA|輸入法漢字模式|
|VK_JUNJA|輸入法 Junja 模式|
|VK_KANA|輸入法 Kana 模式|
|VK_KANJI|輸入法 Kanji 模式|
|VK_LAUNCH_APP1|Windows：啟動應用程式 1 鍵|
|VK_LAUNCH_APP2|Windows：啟動應用程式 2 鍵|
|VK_LAUNCH_MAIL|Windows：啟動郵件鍵|
|VK_LAUNCH_MEDIA_SELECT|Windows：選取媒體按鍵|
|VK_LCONTROL|左 CONTROL 按鍵|
|VK_LMENU|左 MENU 按鍵|
|VK_LSHIFT|左 SHIFT 按鍵|
|VK_MEDIA_NEXT_TRACK|Windows：下一首按鍵|
|VK_MEDIA_PLAY_PAUSE|Windows：播放/暫停媒體按鍵|
|VK_MEDIA_PREV_TRACK|Windows：上一首按鍵|
|VK_MEDIA_STOP|Windows：停止媒體按鍵|
|VK_MODECHANGE|輸入法模式變更要求|
|VK_NONCONVERT|輸入法非轉換|
|VK_OEM_1|Windows：用於美國標準鍵盤 ';:' 索引鍵|
|VK_OEM_102|Windows：角括號索引鍵或 RT 102-key 鍵盤上的反斜線按鍵|
|VK_OEM_2|Windows：用於美國標準鍵盤 '/？' key|
|VK_OEM_3|Windows：用於美國標準鍵盤，' ~' 索引鍵|
|VK_OEM_4|Windows：用於美國標準鍵盤 ' [{' 索引鍵|
|VK_OEM_5|Windows：用於美國標準鍵盤 '\\&#124;' 索引鍵|
|VK_OEM_6|Windows：用於美國標準鍵盤 ']}' 索引鍵|
|VK_OEM_7|Windows：用於美國標準鍵盤 ' 單一-單引號/雙引號 」 按鍵|
|VK_OEM_COMMA|Windows：按鍵用於任何國家/地區，'、'|
|VK_OEM_MINUS|Windows：用於任何國家/地區，'-' 索引鍵|
|VK_OEM_PERIOD|Windows：任何國家/地區，如 '。 ' 索引鍵|
|VK_OEM_PLUS|Windows：按鍵用於任何國家/地區，'+'|
|VK_PACKET|Windows：用來 「 彷彿它們是按鍵輸入傳遞 Unicode 字元。|
|VK_RCONTROL|右 CONTROL 按鍵|
|VK_RMENU|右 MENU 按鍵|
|VK_RSHIFT|右 SHIFT 按鍵|
|VK_SLEEP|電腦睡眠按鍵|
|VK_VOLUME_DOWN|Windows：音量降低鍵|
|VK_VOLUME_MUTE|Windows：靜音鍵|
|VK_VOLUME_UP|Windows：音量提高鍵|
|VK_XBUTTON1|Windows：X1 滑鼠按鈕|
|VK_XBUTTON2|Windows：X2 滑鼠按鈕|

## <a name="accelerator-key-association"></a>快速鍵對應鍵的關聯

您經常想要功能表項目和鍵盤的組合，以發出相同的程式命令。 您可以指派相同的資源識別碼 (ID) 給功能表項目以及應用程式的快速鍵對應表中的項目，即可執行這個動作。 然後，您會編輯功能表項目的標題，以顯示快速鍵的名稱。 如需有關的功能表項目和快速鍵的詳細資訊，請參閱[關聯的快速鍵功能表項目](../windows/associating-a-menu-command-with-an-accelerator-key.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[快速鍵編輯器](../windows/accelerator-editor.md)<br/>