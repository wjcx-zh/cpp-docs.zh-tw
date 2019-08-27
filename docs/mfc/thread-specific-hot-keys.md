---
title: 執行緒特定的熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 49bac6ac357924c26f131bbd8e1092cd74514167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511147"
---
# <a name="thread-specific-hot-keys"></a>執行緒特定的熱鍵

應用程式會使用 Windows `RegisterHotKey`函數來設定執行緒特定的熱鍵 ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md))。 當使用者按下執行緒特定的熱鍵時, Windows 會將[WM_HOTKEY](/windows/win32/inputdev/wm-hotkey)訊息張貼至特定執行緒訊息佇列的開頭。 WM_HOTKEY 訊息包含已按下之特定熱鍵的虛擬按鍵程式碼、移位狀態和使用者定義的識別碼。 如需標準虛擬按鍵代碼的清單, 請參閱 Winuser。 如需此方法的詳細資訊, 請參閱[RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)。

請注意, 在呼叫`RegisterHotKey`中使用的移位狀態旗標與[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)成員函式所傳回的不同, 在呼叫`RegisterHotKey`之前, 您必須先轉譯這些旗標。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
