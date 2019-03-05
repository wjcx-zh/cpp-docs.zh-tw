---
title: 將訊息對應到函式
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 7ed2b66ffe382cc8683b811362fb014597168037
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297680"
---
# <a name="mapping-messages-to-functions"></a>將訊息對應到函式

[屬性] 視窗可讓您將繫結的訊息處理常式 （MFC 使用者介面類別的成員函式） 應用程式的資源所產生的訊息。 它們會使用[MFC 訊息對應](../../mfc/messages-and-commands-in-the-framework.md)建立繫結。

當您使用類別檢視 中建立衍生自其中一個架構類別的新類別時，它會自動放置一個完整且運作正常類別標頭 (.h) 和實作 (.cpp) 中您指定的檔案。

> [!NOTE]
>  若要加入的新類別，不會處理訊息，請直接在文字編輯器中建立的類別。

### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>若要定義或使用 [屬性] 視窗的訊息處理常式中移除

1. 在 [類別檢視] 中，按一下類別。

1. 在 屬性 視窗中，按一下**訊息** 按鈕。

    > [!NOTE]
    >  **訊息**按鈕時，使用您在 類別檢視 或 當您按一下 來源 視窗內選取的類別名稱。

   如果您的專案有一則訊息的處理常式，處理常式的名稱就會出現在右邊的資料行旁邊的訊息。

1. 如果訊息沒有處理常式，然後按一下右側的資料行中顯示建議的處理常式做為名稱的 [屬性] 視窗中的資料格\<加入 >*HandlerName*。 (例如，WM_TIMER 訊息處理常式會建議\<新增 >`OnTimer`)。

1. 按一下建議名稱，新增函式的 Stub 程式碼。

1. 若要編輯訊息處理常式，按兩下 [類別檢視] 中的訊息，並編輯 [來源] 視窗中的程式碼。

若要移除的訊息處理常式，請按兩下右欄中的處理常式，然後選取\<刪除 >*HandlerName*。 這會將函式的程式碼標記為註解。

## <a name="see-also"></a>另請參閱

[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[加入對話方塊控制項的事件處理常式](../../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
