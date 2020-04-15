---
title: 定義反映訊息的訊息處理常式
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365862"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>定義反映訊息的訊息處理常式

創建新的 MFC 控制項類別後,可以為其定義訊息處理程式。 反射的消息處理程序允許控件類在父級收到消息之前處理其自己的消息。 您可以使用 MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函數將消息從控制項發送到父視窗。

例如,藉助此功能,您可以創建一個列表框,該列表框將重新繪製自身,而不是依賴父視窗來執行此操作(繪製所有者)。 有關反射郵件的詳細資訊,請參閱[處理反映的消息](../../mfc/handling-reflected-messages.md)。

要建立具有相同功能的[ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md),必須為 ActiveX 控制件創建專案。

> [!NOTE]
> 不能使用類嚮導為 ActiveX 控件添加反射消息 (OCM_*消息*),如下所述。 您必須手動添加這些消息。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>為來自類精靈的反射訊息定義訊息處理程式

1. 向 MFC 專案添加控制項,如清單、鋼筋控制件、工具列或樹控制件。

1. 在類視圖中,單擊控件類的名稱。

1. 在[類嚮導](mfc-class-wizard.md)中,控制項類名稱將顯示在**類名稱**清單中。

1. 按下「**訊息」** 選項卡以顯示可用於添加到控制項的 Windows 訊息。

1. 選擇要為其定義處理程式的反射消息。 反射的消息用等號 (*) 標記。

1. 按一下類別精靈右列中的儲存格,以新增>\<*處理程式名稱*)顯示處理程式的建議名稱。 ( 例如 **,#WM_CTLCOLOR**訊息\<處理程式建議 新增>**CtlColor**。

1. 單擊要接受的建議名稱。 處理程式將添加到您的專案中。

1. 要編輯或刪除消息處理程式,請重複步驟 4 到 7。 按下包含處理程式名稱的儲存格以編輯或刪除,然後單擊相應的任務。

## <a name="see-also"></a>另請參閱

[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)
