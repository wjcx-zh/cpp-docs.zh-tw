---
title: 與使用者介面物件關聯的訊息類型
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.uiobject.msgs
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
ms.openlocfilehash: 1676edf487d536d75ccd7901c5bdfa827cc143fe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326318"
---
# <a name="message-types-associated-with-user-interface-objects"></a>與使用者介面物件關聯的訊息類型

下表顯示類型的物件，用來處理，以及與其相關聯的訊息類型。

### <a name="user-interface-objects-and-associated-messages"></a>使用者介面物件和相關聯的訊息

|物件識別碼|訊息|
|---------------|--------------|
|代表包含視窗的類別名稱|適當的 Windows 訊息[CWnd](../../mfc/reference/cwnd-class.md)-衍生的類別： 對話方塊、 視窗、 子視窗、 MDI 子視窗或最上層框架視窗。|
|功能表或快速鍵的識別項|命令訊息 （執行程式函式）。<br />-UPDATE_COMMAND_UI 訊息 （動態更新功能表項目）。|
|控制項識別項|選取的控制項類型的控制項通知訊息。|

## <a name="see-also"></a>另請參閱

[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
