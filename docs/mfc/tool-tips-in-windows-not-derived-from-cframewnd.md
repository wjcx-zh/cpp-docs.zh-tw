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
ms.openlocfilehash: 3d44f2c503b689360f040e6804d319c331d5c0ca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260656"
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>非衍生自 CFrameWnd 之視窗中的工具提示

此系列的文章涵蓋包含在視窗中，不衍生自控制項啟用工具提示[CFrameWnd](../mfc/reference/cframewnd-class.md)。 發行項[工具列工具提示](../mfc/toolbar-tool-tips.md)中的控制項提供工具提示資訊`CFrameWnd`。

在此系列的文章中涵蓋的主題包括：

- [啟用工具提示](../mfc/enabling-tool-tips.md)

- [處理工具提示的 TTN_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)

- [TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)

工具提示會自動顯示按鈕，並包含在父視窗中其他控制項衍生自`CFrameWnd`。 這是因為`CFrameWnd`有的預設處理常式[TTN_GETDISPINFO](/windows/desktop/Controls/ttn-getdispinfo)通知，用來處理**TTN_NEEDTEXT**通知從工具提示與控制項相關聯的控制項。

不過，這個預設處理常式不會呼叫的時機**TTN_NEEDTEXT**時傳送通知，從 工具提示控制項的視窗中，不是控制項相關聯`CFrameWnd`，例如對話方塊或 表單 檢視上的控制項。 因此，就必須為您提供的處理常式函式**TTN_NEEDTEXT**通知訊息，以顯示子控制項的工具提示。

針對您的 windows 所提供的預設工具提示[CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips)沒有與其相關聯的文字。 若要擷取要顯示的工具提示的文字**TTN_NEEDTEXT**在顯示工具提示視窗之前，將會傳送至工具提示控制項的父視窗的通知。 如果沒有將一些值指派給這個訊息處理常式*pszText*隸屬**TOOLTIPTEXT**結構，會有任何工具提示所顯示的文字。

## <a name="see-also"></a>另請參閱

[工具提示](../mfc/tool-tips.md)
