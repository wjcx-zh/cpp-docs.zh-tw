---
title: 搭配使用對話方塊列與 Rebar 控制項
ms.date: 11/04/2016
f1_keywords:
- WM_EX_TRANSPARENT
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: 33ca3d0a7bf2e60511ea0048ad91b1f0930a2894
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287171"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>搭配使用對話方塊列與 Rebar 控制項

中所述[Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)，每個群組列可以包含只有一個子視窗 （或控制項）。 如果您想要有一個以上的子視窗，每一個團隊，這可能是一項限制。 方便的因應措施是使用多個控制項建立對話方塊列資源，然後在 rebar 控制項中新增 rebar 群組列 （包含對話方塊列）。

一般來說，如果您想要顯示透明對話方塊列頻外，您會設定 WS_EX_TRANSPARENT 延伸對話方塊列物件的樣式。 不過，由於 WS_EX_TRANSPARENT 具有正確繪製背景對話方塊列的一些問題，您必須執行一些額外的工作，以達到所需的效果。

下列程序詳細資料，而不需使用 WS_EX_TRANSPARENT 達到透明度所需的步驟延伸樣式。

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>若要實作 rebar 群組列中的透明對話方塊列

1. 使用[加入類別對話方塊](../mfc/reference/adding-an-mfc-class.md)，加入新的類別 (例如`CMyDlgBar`) 實作您的對話方塊列物件。

1. 新增 WM_ERASEBKGND 訊息處理常式。

1. 在新的處理常式中，修改現有的程式碼，以符合下列範例：

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. 新增 WM_MOVE 訊息處理常式。

1. 在新的處理常式中，修改現有的程式碼，以符合下列範例：

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

新的處理常式來模擬對話方塊列的透明度 WM_ERASEBKGND 訊息轉送至父視窗，並強制重新繪製，每次移動對話方塊列物件。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
