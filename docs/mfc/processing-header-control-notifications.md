---
title: 處理標題控制項告知
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
ms.openlocfilehash: 3c5d147741123f97a53b18a854db9204738d0a2f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339614"
---
# <a name="processing-header-control-notifications"></a>處理標題控制項告知

在檢視或對話方塊類別中，使用 [屬性] 視窗來建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的任何標頭控制項使用的處理常式函式 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 您想要的通知訊息處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。 通知會傳送至父視窗中，當使用者按一下或按兩下標頭項目，拖曳分割線之間的項目，依此類推。

標頭控制項相關聯的通知訊息所述[標頭控制項參考](/windows/desktop/controls/header-control-reference)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
