---
title: CStatusBarCtrl 的設定
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446395"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的設定

[ [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)狀態] 視窗的預設位置沿著父視窗的底部，但您可以指定 CCS_TOP 樣式，讓它出現在父視窗的工作區頂端。

您可以指定 SBARS_SIZEGRIP 樣式，以在 [`CStatusBarCtrl` 狀態] 視窗的右端包含調整大小的底框。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

> [!NOTE]
>  如果您結合 CCS_TOP 和 SBARS_SIZEGRIP 樣式，則即使系統將它繪製在狀態視窗中，產生的調整大小的底框還是無法運作。

狀態視窗的視窗程序會自動設定控制項視窗的初始大小和位置。 這個寬度與父視窗工作區的寬度相同。 高度根據目前選取到狀態視窗的裝置內容的字型度量資訊和視窗框線寬度。

視窗程式會在收到 WM_SIZE 訊息時，自動調整狀態視窗的大小。 一般而言，當父視窗的大小變更時，父系會將 WM_SIZE 訊息傳送至狀態視窗。

您可以藉由呼叫[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)，指定最小高度（以圖元為單位），以設定狀態視窗繪製區域的最小高度。 繪圖區域不包括視窗框線。

您可以藉由呼叫[可以 getborders 擷取](../mfc/reference/cstatusbarctrl-class.md#getborders)來取得狀態視窗的框線寬度。 此成員函式包含三元素陣列的指標，會接收水平框線、垂直框線和矩形間框線的寬度。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
