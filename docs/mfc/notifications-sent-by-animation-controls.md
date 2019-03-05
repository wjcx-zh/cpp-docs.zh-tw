---
title: 動畫控制項傳送的告知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 2a736e4315091b1b26daceb4fe0ce9672ab33ff6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281261"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知

動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送兩種不同的通知訊息。 傳送通知的形式[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息。

[ACN_START](/windows/desktop/Controls/acn-start)當動畫控制項開始播放短片時，傳送訊息。 [ACN_STOP](/windows/desktop/Controls/acn-stop)動畫控制項完成或停止播放短片時，會傳送訊息。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
