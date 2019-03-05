---
title: 處理工具提示告知
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 079dc26fdd355c5b5e3f89f28219902e5fd74a79
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268820"
---
# <a name="handling-tool-tip-notifications"></a>處理工具提示告知

當您指定**TBSTYLE_TOOLTIPS**樣式工具列會建立和管理工具提示控制項。 工具提示是文字的小型的快顯視窗，其中包含描述工具列按鈕行。 工具提示是隱藏的才會出現僅當使用者將游標放在工具列按鈕上等待它那里大約半秒。 工具提示會顯示游標周圍。

工具提示隨即出現之前，請**TTN_NEEDTEXT**通知訊息時，會傳送至工具列的擁有者視窗上，以擷取按鈕的描述性文字。 工具列的主控視窗是否`CFrameWnd`視窗中，工具提示會顯示而不需要任何額外的工作，因為`CFrameWnd`具有預設處理常式**TTN_NEEDTEXT**通知。 如果工具列的擁有者視窗不衍生自`CFrameWnd`，例如對話方塊或表單檢視，您必須將項目加入至主控視窗的訊息對應，並提供訊息對應中的通知處理常式。 主控視窗的訊息對應的項目如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>備註

*memberFxn*<br/>
此按鈕需要文字時要呼叫此成員函式。

請注意，工具提示的識別碼一律為 0。

除了**TTN_NEEDTEXT**通知，工具提示控制項可以傳送下列通知給工具列控制項：

|通知|意義|
|------------------|-------------|
|**TTN_NEEDTEXTA**|工具提示控制項需要 ASCII 文字 (Windows 95)|
|**TTN_NEEDTEXTW**|工具提示控制項需要 UNICODE 文字 (Windows NT)|
|**TBN_HOTITEMCHANGE**|指出已變更的經常性存取 （反白顯示） 項目。|
|**NM_RCLICK**|表示使用者已經以滑鼠右鍵按一下按鈕。|
|**TBN_DRAGOUT**|表示使用者已按下按鈕並拖曳出按鈕的指標。 它可讓應用程式實作拖放和卸除從工具列按鈕。 當收到此通知，應用程式將會開始拖曳，並卸除作業。|
|**TBN_DROPDOWN**|表示使用者已按一下使用的按鈕**TBSTYLE_DROPDOWN**樣式。|
|**TBN_GETOBJECT**|表示使用者將滑鼠指標移使用的按鈕**TBSTYLE_DROPPABLE**樣式。|

範例處理常式函式及啟用工具提示的詳細資訊，請參閱[工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
