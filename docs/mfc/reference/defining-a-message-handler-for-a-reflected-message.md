---
title: 定義反映訊息的訊息處理常式
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907934"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>定義反映訊息的訊息處理常式

當您建立新的 MFC 控制項類別之後，就可以為它定義訊息處理常式。 反映的訊息處理常式可讓您的控制項類別在父系收到訊息之前，先處理自己的訊息。 您可以使用 MFC [CWnd：： SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)函式，將訊息從控制項傳送至父視窗。

例如，您可以使用這項功能來建立清單方塊，以重新繪製本身，而不是依賴父視窗來執行此動作（已繪製擁有者）。 如需反映訊息的詳細資訊，請參閱[處理反映的訊息](../../mfc/handling-reflected-messages.md)。

若要建立具有相同功能的[activex 控制項](../../mfc/activex-controls-on-the-internet.md)，您必須建立 activex 控制項的專案。

> [!NOTE]
>  您無法使用類別 Wizard 為 ActiveX 控制項加入反映的訊息（OCM_*訊息*），如下所述。 您必須手動新增這些訊息。

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>若要從類別 Wizard 定義反映訊息的訊息處理常式

1. 將控制項（例如清單、Rebar 控制項、工具列或樹狀目錄控制項）新增至您的 MFC 專案。

1. 在類別檢視中，按一下控制項類別的名稱。

1. 在[類別 Wizard](mfc-class-wizard.md)中，控制項類別名稱會出現在 [**類別名稱**] 清單中。

1. 按一下 [**訊息**] 索引標籤，顯示可新增至控制項的 Windows 訊息。

1. 選取您要定義處理常式的反映訊息。 反映的訊息會以等號（=）標示。

1. 按一下 [類別] [Wizard] 右邊資料行中的資料格，將建議的處理常式\<名稱顯示為 add >*HandlerName*。 （例如， **= WM_CTLCOLOR**訊息處理常式建議\<add >**CTLCOLOR**）。

1. 按一下建議的名稱以接受。 處理常式會加入至您的專案。

1. 若要編輯或刪除訊息處理常式，請重複步驟4到7。 按一下包含要編輯或刪除之處理常式名稱的資料格，然後按一下適當的工作。

## <a name="see-also"></a>另請參閱

[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)
