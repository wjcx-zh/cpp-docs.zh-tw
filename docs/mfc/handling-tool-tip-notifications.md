---
title: 處理工具提示告知
ms.date: 11/04/2016
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
ms.openlocfilehash: 41e3dbfc2269f5fbf3c12dc00c19f8a2253fd16a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626438"
---
# <a name="handling-tool-tip-notifications"></a>處理工具提示告知

當您指定**TBSTYLE_TOOLTIPS**樣式時，工具列會建立並管理工具提示控制項。 工具提示是一個小型快顯視窗，其中包含描述工具列按鈕的一行文字。 工具提示是隱藏的，只有當使用者將游標放在工具列按鈕上，並將它留在大約一秒的時間時，才會出現。 工具提示會顯示在游標附近。

在顯示工具提示之前，會將**TTN_NEEDTEXT**通知訊息傳送至工具列的 [擁有者] 視窗，以取得按鈕的描述性文字。 如果工具列的 [擁有者] 視窗是 `CFrameWnd` 視窗，則會顯示工具提示，而不會進行任何額外的工作，因為 `CFrameWnd` 具有**TTN_NEEDTEXT**通知的預設處理常式。 如果工具列的 [擁有者] 視窗並非衍生自（ `CFrameWnd` 例如對話方塊或表單檢視），您就必須在擁有者視窗的訊息對應中加入專案，並在訊息對應中提供通知處理常式。 您的主控視窗訊息對應的專案如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]

## <a name="remarks"></a>備註

*memberFxn*<br/>
當此按鈕需要文字時，所要呼叫的成員函式。

請注意，工具提示的識別碼一律為0。

除了**TTN_NEEDTEXT**通知以外，工具提示控制項也可以將下列通知傳送至工具列控制項：

|通知|意義|
|------------------|-------------|
|**TTN_NEEDTEXTA**|工具提示控制項需要 ASCII 文字（僅限 Windows 95）|
|**TTN_NEEDTEXTW**|工具提示控制項需要 UNICODE 文字（僅限 Windows NT）|
|**TBN_HOTITEMCHANGE**|表示熱（反白顯示）專案已變更。|
|**NM_RCLICK**|表示使用者已以滑鼠右鍵按一下按鈕。|
|**TBN_DRAGOUT**|表示使用者已按一下按鈕，並將指標拖曳至按鈕。 它可讓應用程式從工具列按鈕執行拖放功能。 收到此通知時，應用程式會開始拖放作業。|
|**TBN_DROPDOWN**|表示使用者已按一下使用**TBSTYLE_DROPDOWN**樣式的按鈕。|
|**TBN_GETOBJECT**|表示使用者已將指標移到使用**TBSTYLE_DROPPABLE**樣式的按鈕上方。|

如需範例處理常式函式以及啟用工具提示的詳細資訊，請參閱[工具提示](tool-tips-in-windows-not-derived-from-cframewnd.md)。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控制項](controls-mfc.md)
