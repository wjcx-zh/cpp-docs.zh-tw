---
title: CStatusBarCtrl 的設定
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365371"
---
# <a name="settings-for-the-cstatusbarctrl"></a>CStatusBarCtrl 的設定

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)狀態視窗的預設位置位於父視窗的底部,但您可以指定CCS_TOP樣式,使其顯示在父視窗的工作區的頂部。

您可以指定SBARS_SIZEGRIP樣式,以在`CStatusBarCtrl`狀態視窗的右端包括大小調整夾。 調整大小的底框類似縮放框線；它是使用者可以按一下並拖曳調整父視窗大小的矩形區域。

> [!NOTE]
> 如果將CCS_TOP和SBARS_SIZEGRIP樣式組合在一起,則即使系統在狀態視窗中繪製,生成的大小調整夾點也不會正常工作。

狀態視窗的視窗程序會自動設定控制項視窗的初始大小和位置。 這個寬度與父視窗工作區的寬度相同。 高度根據目前選取到狀態視窗的裝置內容的字型度量資訊和視窗框線寬度。

視窗過程在接收WM_SIZE消息時自動調整狀態視窗的大小。 通常,當父視窗的大小發生變化時,父視窗向狀態視窗發送WM_SIZE消息。

您可以通過調用[SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight)來設定狀態視窗繪圖區域的最小高度,指定最小高度(以像素為單位)。 繪圖區域不包括視窗框線。

通過調用[GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders)來檢索狀態視窗邊框的寬度。 此成員函式包含三元素陣列的指標，會接收水平框線、垂直框線和矩形間框線的寬度。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
