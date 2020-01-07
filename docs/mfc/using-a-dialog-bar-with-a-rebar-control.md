---
title: 搭配使用對話方塊列與 Rebar 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: e4e786d3670ec74b734739e29aa7e3e33b5af384
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302363"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>搭配使用對話方塊列與 Rebar 控制項

如[Rebar 控制項和頻帶](../mfc/rebar-controls-and-bands.md)中所述，每個寬線只能包含一個子視窗（或控制項）。 如果您想要每個波段有一個以上的子視窗，這可能是一項限制。 方便的解決方法是建立具有多個控制項的對話方塊列資源，然後將 Rebar 寬線（包含對話方塊列）新增至 Rebar 控制項。

一般來說，如果您想要讓對話列區顯示為透明，您會設定對話方塊列物件的 WS_EX_TRANSPARENT 擴充樣式。 不過，因為 WS_EX_TRANSPARENT 在適當繪製對話方塊列的背景時發生一些問題，所以您需要執行一些額外的工作，以達到所要的效果。

下列程式詳細說明在沒有使用 WS_EX_TRANSPARENT 擴充樣式的情況下，達到透明度所需的步驟。

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>在 Rebar 寬線中執行透明的對話方塊列

1. 使用 [[加入類別] 對話方塊](../mfc/reference/adding-an-mfc-class.md)，加入可執行對話方塊列物件的新類別（例如，`CMyDlgBar`）。

1. 新增 WM_ERASEBKGND 訊息的處理常式。

1. 在新的處理常式中，修改現有的程式碼以符合下列範例：

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. 新增 WM_MOVE 訊息的處理常式。

1. 在新的處理常式中，修改現有的程式碼以符合下列範例：

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

新的處理常式會藉由將 WM_ERASEBKGND 訊息轉送到父視窗，並在每次移動對話方塊列物件時強制重新繪製，來模擬對話方塊列的透明度。

## <a name="see-also"></a>請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
