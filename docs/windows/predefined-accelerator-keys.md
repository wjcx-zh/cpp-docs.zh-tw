---
title: 預先定義的快速鍵 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts, predefined
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa5b42fc846f3b4f21dc8045e67d8ebc347601ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880791"
---
# <a name="predefined-accelerator-keys"></a>預先定義的快速鍵
Windows 應用程式專案中可能包含許多預先定義的快速鍵。 其中有部分是用於 Windows 環境的虛擬按鍵。 其他則支援瀏覽器或 Unicode 應用程式。 您可以在任何加速器中使用任何此類按鍵。  
  
|Key|描述|  
|---------|-----------------|  
|VK_ACCEPT|IME accept|  
|VK_BROWSER_BACK|Windows：瀏覽器上一頁按鍵|  
|VK_BROWSER_FAVORITES|Windows：瀏覽器我的最愛按鍵|  
|VK_BROWSER_FORWARD|Windows：瀏覽器下一頁按鍵|  
|VK_BROWSER_HOME|Windows：瀏覽器啟動和首頁按鍵|  
|VK_BROWSER_REFRESH|Windows：瀏覽器重新整理按鍵|  
|VK_BROWSER_SEARCH|Windows：瀏覽器搜尋按鍵|  
|VK_BROWSER_STOP|Windows：瀏覽器停止按鍵|  
|VK_CONVERT|輸入法轉換|  
|VK_FINAL|輸入法最終模式|  
|VK_HANGUEL|輸入法 Hanguel 模式 (維護相容性；使用 VK_HANGUL)|  
|VK_HANGUL|輸入法韓文模式|  
|VK_HANJA|輸入法漢字模式|  
|VK_JUNJA|輸入法 Junja 模式|  
|VK_KANA|輸入法 Kana 模式|  
|VK_KANJI|輸入法 Kanji 模式|  
|VK_LAUNCH_APP1|Windows：啟動應用程式 1 按鍵|  
|VK_LAUNCH_APP2|Windows：啟動應用程式 2 按鍵|  
|VK_LAUNCH_MAIL|Windows：啟動郵件按鍵|  
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
|VK_OEM_1|Windows：';:' 按鍵用於美國標準鍵盤|  
|VK_OEM_102|Windows：RT 102-key 鍵盤上的角括號按鍵或反斜線按鍵|  
|VK_OEM_2|Windows： 用於美國標準鍵盤 '/？' key|  
|VK_OEM_3|Windows：'`~' 按鍵用於美國標準鍵盤|  
|VK_OEM_4|Windows：'[{' 按鍵用於美國標準鍵盤|  
|VK_OEM_5|Windows： 用於美國標準鍵盤 '\\&#124;' 金鑰|  
|VK_OEM_6|Windows：']}' 按鍵用於美國標準鍵盤|  
|VK_OEM_7|Windows：「單引號/雙引號」按鍵用於美國標準鍵盤|  
|VK_OEM_COMMA|Windows：',' 按鍵用於任何國家/地區|  
|VK_OEM_MINUS|Windows：'-' 按鍵用於任何國家/地區|  
|VK_OEM_PERIOD|Windows：'.' 按鍵用於任何國家/地區|  
|VK_OEM_PLUS|Windows：'+' 按鍵用於任何國家/地區|  
|VK_PACKET|Windows：用來將 Unicode 字元視為按鍵輸入傳遞。|  
|VK_RCONTROL|右 CONTROL 按鍵|  
|VK_RMENU|右 MENU 按鍵|  
|VK_RSHIFT|右 SHIFT 按鍵|  
|VK_SLEEP|電腦睡眠按鍵|  
|VK_VOLUME_DOWN|Windows：降低音量按鍵|  
|VK_VOLUME_MUTE|Windows：靜音按鍵|  
|VK_VOLUME_UP|Windows：提高音量按鍵|  
|VK_XBUTTON1|Windows：X1 滑鼠按鈕|  
|VK_XBUTTON2|Windows：X2 滑鼠按鈕|  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。*  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵編輯器](../windows/accelerator-editor.md)   
 [資源編輯器](../windows/resource-editors.md)