---
title: 強制回應和非強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: d3497a19ab14dcc9f14dc0419eb65ea033135b6e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508857"
---
# <a name="modal-and-modeless-dialog-boxes"></a>強制回應和非強制回應對話方塊

您可以使用 [類別 [CDialog](reference/cdialog-class.md) ] 來管理兩種對話方塊：

- *強制回應對話方塊*，要求使用者在繼續程式之前回應

- 非*強制回應對話方塊*，會留在畫面上，隨時可供使用，但允許其他使用者活動

用於建立對話方塊範本的資源編輯和程式，與強制回應和非強制回應對話方塊相同。

為您的程式建立對話方塊需要執行下列步驟：

1. 使用 [對話方塊編輯器](../windows/dialog-editor.md) 來設計對話方塊，並建立其對話方塊範本資源。

1. 建立對話方塊類別。

1. 將 [對話方塊資源的控制項連接至](../windows/adding-editing-or-deleting-controls.md) dialog 類別中的訊息處理常式。

1. 加入與對話方塊的控制項相關聯的資料成員，以及指定控制項的 [對話方塊資料交換](dialog-data-exchange.md) 和 [對話資料驗證](dialog-data-validation.md) 。

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
