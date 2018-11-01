---
title: 動畫控制項傳送的告知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 8c437e6950435b49c280c4f1bb9225002545d6f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449292"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知

動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送兩種不同的通知訊息。 傳送通知的形式[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息。

[ACN_START](/windows/desktop/Controls/acn-start)當動畫控制項開始播放短片時，傳送訊息。 [ACN_STOP](/windows/desktop/Controls/acn-stop)動畫控制項完成或停止播放短片時，會傳送訊息。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

