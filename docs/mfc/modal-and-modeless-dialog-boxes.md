---
title: 強制回應和非強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 886229a2b66968bf76129ecb1da838bd36e66215
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685186"
---
# <a name="modal-and-modeless-dialog-boxes"></a>強制回應和非強制回應對話方塊

您可以使用 [類別[CDialog](../mfc/reference/cdialog-class.md) ] 來管理兩種對話方塊：

- *強制回應對話方塊*，要求使用者在繼續程式之前回應

- 非*強制回應對話方塊*會停留在畫面上，並可隨時使用，但允許其他使用者活動

[資源編輯] 和 [建立對話方塊範本的程式] 與 [模式] 和 [非模式] 對話方塊都相同。

建立程式的對話方塊需要執行下列步驟：

1. 使用[對話方塊編輯器](../windows/dialog-editor.md)來設計對話方塊，並建立其對話方塊範本資源。

1. 建立對話方塊類別。

1. 將[對話方塊資源的控制項連接至](../windows/adding-event-handlers-for-dialog-box-controls.md)對話方塊類別中的訊息處理常式。

1. 加入與對話方塊控制項相關聯的資料成員，並指定控制項的[對話方塊資料交換](../mfc/dialog-data-exchange.md)和[對話方塊資料驗證](../mfc/dialog-data-validation.md)。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
