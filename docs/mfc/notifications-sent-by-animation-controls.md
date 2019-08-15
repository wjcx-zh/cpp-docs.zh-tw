---
title: 動畫控制項傳送的告知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
ms.openlocfilehash: 68ede3bc55669a29eef192d38b29b8c1ab433e4b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508021"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知

動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送兩種不同類型的通知訊息。 通知會以[WM_COMMAND](/windows/win32/menurc/wm-command)訊息的形式傳送。

當動畫控制項已開始播放剪輯時, 就會傳送[ACN_START](/windows/win32/Controls/acn-start)訊息。 當動畫控制項已完成或停止播放剪輯時, 就會傳送[ACN_STOP](/windows/win32/Controls/acn-stop)訊息。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
