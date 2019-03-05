---
title: 樹狀目錄控制項通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 90e2e112d7862dfed7d8af31cfb72ff45633a2c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278391"
---
# <a name="tree-control-notification-messages"></a>樹狀目錄控制項通知訊息

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 以 WM_NOTIFY 訊息中傳送下列通知訊息：

|通知訊息|描述|
|--------------------------|-----------------|
|TVN_BEGINDRAG|表示在拖放作業的開始|
|TVN_BEGINLABELEDIT|表示在就地標籤編輯|
|TVN_BEGINRDRAG|表示使用滑鼠右按鈕拖放作業的開始|
|TVN_DELETEITEM|表示特定項目的刪除|
|TVN_ENDLABELEDIT|表示結尾標籤編輯|
|TVN_GETDISPINFO|要求的要求資訊，樹狀目錄控制項來顯示項目|
|TVN_ITEMEXPANDED|父項目的子項目清單已展開或摺疊的訊號|
|TVN_ITEMEXPANDING|訊號的父項目的子項目清單將要展開或摺疊|
|TVN_KEYDOWN|表示鍵盤事件|
|TVN_SELCHANGED|選取項目已從一個項目變更為另一個的訊號|
|TVN_SELCHANGING|選取項目即將從一個項目變更為另一個的訊號|
|TVN_SETDISPINFO|若要更新的項目所維護的資訊的通知|

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
