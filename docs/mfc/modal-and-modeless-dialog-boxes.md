---
title: 強制回應和非強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 7e1dc9c40f60dc46117ee0673a038d5a63df7680
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528358"
---
# <a name="modal-and-modeless-dialog-boxes"></a>強制回應和非強制回應對話方塊

您可以使用類別[CDialog](../mfc/reference/cdialog-class.md)來管理兩種類型的對話方塊：

- *強制回應對話方塊*，這需要使用者回應之前繼續執行程式

- *非強制回應對話方塊*，其中留在畫面和可供您在任何時候使用，但允許其他使用者的活動

資源編輯和建立對話方塊範本的程序也適用於強制回應和非強制回應對話方塊。

建立對話方塊中，為您的程式需要下列步驟：

1. 使用[對話方塊編輯器](../windows/dialog-editor.md)設計對話方塊，並建立其對話方塊範本資源。

1. 建立對話方塊類別。

1. 連接[對話方塊資源的控制訊息處理常式來](../windows/adding-event-handlers-for-dialog-box-controls.md)對話方塊類別中。

1. 加入與對話方塊的控制項，並指定相關聯的資料成員[對話資料交換](../mfc/dialog-data-exchange.md)並[對話方塊資料驗證](../mfc/dialog-data-validation.md)的控制項。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

