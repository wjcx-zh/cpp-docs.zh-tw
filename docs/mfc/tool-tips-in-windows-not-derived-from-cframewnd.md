---
title: 非衍生自 CFrameWnd 之視窗中的工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
ms.openlocfilehash: 1f68fb62335219ea498163e6124c8e91e49f2938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511032"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>非衍生自 CFrameWnd 之視窗中的工具提示

本文系列涵蓋的工具提示, 可讓您在不是衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md)的視窗中包含控制項。 文章[工具列工具提示](../mfc/toolbar-tool-tips.md)提供中`CFrameWnd`控制項的工具提示的相關資訊。

本文系列涵蓋的主題包括:

- [啟用工具提示](../mfc/enabling-tool-tips.md)

- [處理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)

從衍生自之`CFrameWnd`父視窗中包含的按鈕和其他控制項, 會自動顯示工具提示。 這是因為`CFrameWnd`具有[TTN_GETDISPINFO](/windows/win32/Controls/ttn-getdispinfo)通知的預設處理常式, 它會處理與控制項相關聯的工具提示控制項中的**TTN_NEEDTEXT**通知。

不過, 當**TTN_NEEDTEXT**通知是從不是的`CFrameWnd`視窗 (例如對話方塊或表單檢視中的控制項) 所關聯的工具提示控制項傳送時, 不會呼叫這個預設處理常式。 因此, 您必須提供**TTN_NEEDTEXT**通知訊息的處理常式函式, 才能顯示子控制項的工具提示。

提供給 windows 的[CWnd:: EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)的預設工具提示沒有相關聯的文字。 若要取得工具提示顯示的文字, 在顯示工具提示視窗之前, **TTN_NEEDTEXT**通知會傳送至工具提示控制項的父視窗。 如果此訊息沒有處理常式可將某個值指派給**TOOLTIPTEXT**結構的*pszText*成員, 則工具提示不會顯示任何文字。

## <a name="see-also"></a>另請參閱

[工具提示](../mfc/tool-tips.md)
