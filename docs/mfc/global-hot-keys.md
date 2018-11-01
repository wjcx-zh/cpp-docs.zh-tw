---
title: 全域熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 4cafee311f71d8165380b3fb7e192e7032b7941c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529931"
---
# <a name="global-hot-keys"></a>全域熱鍵

全域熱鍵是與特定藉視窗相關聯。 它可讓使用者啟動的視窗，從系統的任何部分。 應用程式設定所傳送的特定視窗的全域快速鍵[WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey)至該視窗的訊息。 比方說，如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)物件和`pMainWnd`是指標，要在按下便捷鍵時啟動視窗，您可以使用下列程式碼來建立快速鍵與控制項中所指定的關聯視窗所指的`pMainWnd`。

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

每當使用者按下的全域快速鍵，指定視窗會收到[WM_SYSCOMMAND](/windows/desktop/menurc/wm-syscommand)指定的訊息**SC_HOTKEY**做為命令的類型。 此訊息也會啟用接收視窗。 此訊息不包含任何有關已按下的確切索引鍵，因為使用此方法不允許區別不同的快速鍵可能會附加到相同的視窗。 熱鍵之前會保持有效傳送的應用程式**WM_SETHOTKEY**結束。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

