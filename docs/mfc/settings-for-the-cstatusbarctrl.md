---
title: CStatusBarCtrl 的設定
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: b41997fb9342a651260bc2196d212016dc0deb7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307688"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的設定

預設位置[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)狀態視窗是在父視窗的底部，但是您可以指定讓它出現在父視窗工作區頂端的 CCS_TOP 樣式。

您可以指定要包含的右端的調整大小底框的 SBARS_SIZEGRIP 樣式`CStatusBarCtrl`狀態視窗。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

> [!NOTE]
>  如果您結合 CCS_TOP 和 SBARS_SIZEGRIP 樣式時，產生的調整大小底框不能運作即使系統將它繪製在狀態視窗。

狀態視窗的視窗程序會自動設定控制項視窗的初始大小和位置。 這個寬度與父視窗工作區的寬度相同。 高度根據目前選取到狀態視窗的裝置內容的字型度量資訊和視窗框線寬度。

視窗程序會接收 WM_SIZE 訊息時，會自動調整狀態視窗的大小。 通常，父視窗的大小變更時，父代就會傳送 WM_SIZE 訊息在狀態視窗。

您可以藉由呼叫設定狀態視窗的繪圖區域的最小高度[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)，像素為單位指定的最小高度。 繪圖區域不包括視窗框線。

呼叫擷取狀態視窗的框線寬度[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)。 此成員函式包含三元素陣列的指標，會接收水平框線、垂直框線和矩形間框線的寬度。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
