---
title: 使用 CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447100"
---
# <a name="using-canimatectrl"></a>使用 CAnimateCtrl

由類別[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)代表的動畫控制項，是以音訊影片交錯（AVI）格式（標準 Windows Video/音訊格式）顯示剪輯的視窗。 AVI 短片是一系列的點陣圖框架，例如電影。

因為在播放 AVI 短片的同時，您的執行緒會繼續執行，因此動畫控制項的常見用法之一是在長時間作業期間表示系統的活動。 例如，[Windows 搜尋] 對話方塊會隨著系統搜尋檔案而顯示一個移動的放大鏡。

動畫控制項只能播放簡單的 AVI 短片，且不支援音效 （如需限制的完整清單，請參閱[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)）。由於動畫控制項的功能受到嚴格限制，而且可能會變更，因此如果您需要控制項來提供多媒體播放和/或記錄功能，您應該使用替代方法，例如 MCIWnd 控制項。 如需 MCIWnd 控制項的詳細資訊，請參閱多媒體文件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [使用動畫控制項](../mfc/using-an-animation-control.md)

- [動畫控制項傳送的通知](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)
