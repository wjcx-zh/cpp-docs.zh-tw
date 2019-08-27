---
title: 全域熱鍵
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 59918648ea24fd1e2a86ca786de3081cd6cca2df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508558"
---
# <a name="global-hot-keys"></a>全域熱鍵

全域熱鍵會與特定的 nonchild 視窗相關聯。 它可讓使用者從系統的任何部分啟動視窗。 應用程式會將[WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey)訊息傳送至該視窗, 以設定特定視窗的全域熱鍵。 例如, 如果`m_HotKeyCtrl`是[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)物件, 而且`pMainWnd`是按下快速鍵時要啟動之視窗的指標, 您可以使用下列程式碼, 將控制項中指定的熱鍵與所指向的視窗產生關聯`pMainWnd`.

[!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/cpp/global-hot-keys_1.cpp)]

每當使用者按下全域熱鍵時, 指定的視窗就會收到指定**SC_HOTKEY**做為命令類型的[WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand)訊息。 此訊息也會啟用接收它的視窗。 因為此訊息不包含所按的確切索引鍵上的任何資訊, 所以使用這個方法不允許區別可能附加至相同視窗的不同快速鍵。 熱鍵會一直有效, 直到傳送**WM_SETHOTKEY**的應用程式結束為止。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
