---
title: 動畫控制項傳送的告知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: e9e5b94736de44d5cfeef81f5b78a759df3b8aa0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619915"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知

動畫控制項（[CAnimateCtrl](reference/canimatectrl-class.md)）會傳送兩種不同類型的通知訊息。 通知會以[WM_COMMAND](/windows/win32/menurc/wm-command)訊息的形式傳送。

當動畫控制項已開始播放剪輯時，就會傳送[ACN_START](/windows/win32/Controls/acn-start)訊息。 當動畫控制項已完成或停止播放剪輯時，就會傳送[ACN_STOP](/windows/win32/Controls/acn-stop)訊息。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](using-canimatectrl.md)<br/>
[控制項](controls-mfc.md)
