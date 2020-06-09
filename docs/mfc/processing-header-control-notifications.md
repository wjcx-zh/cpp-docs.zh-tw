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
ms.openlocfilehash: c313382b8be7538ba5bb465c6ba383955e414662
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619799"
---
# <a name="processing-header-control-notifications"></a>處理標題控制項告知

在您的 view 或 dialog 類別中，使用[類別 Wizard](reference/mfc-class-wizard.md)來建立[OnChildNotify](reference/cwnd-class.md#onchildnotify)處理常式函式，其中包含您想要處理的任何標頭控制項（[CHeaderCtrl](reference/cheaderctrl-class.md)）通知訊息的 Switch 語句（請參閱[將訊息對應至](reference/mapping-messages-to-functions.md)函式）。 當使用者按一下或按兩下標題專案、在專案之間拖曳分隔線等等時，通知就會傳送至父視窗。

與標題控制項相關聯的通知訊息會列在 Windows SDK 的[標題控制項參考](/windows/win32/controls/header-control-reference)中。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](using-cheaderctrl.md)<br/>
[控制項](controls-mfc.md)
