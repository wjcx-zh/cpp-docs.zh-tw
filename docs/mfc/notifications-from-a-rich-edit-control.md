---
title: 來自 Rich Edit 控制項的告知
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: 206fc02088f6531338bf2aa4cf272a1da096bae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622219"
---
# <a name="notifications-from-a-rich-edit-control"></a>來自 Rich Edit 控制項的告知

通知訊息會報告影響 rich edit 控制項（[CRichEditCtrl](reference/cricheditctrl-class.md)）的事件。 它們可以由父視窗處理，或使用訊息反映，由 rich edit 控制項本身來處理。 Rich edit 控制項支援所有與編輯控制項搭配使用的通知訊息，以及其他幾個。 您可以藉由設定其「事件遮罩」，判斷 rich edit 控制項傳送其父視窗的通知訊息。

若要設定 rich edit 控制項的事件遮罩，請使用[SetEventMask](reference/cricheditctrl-class.md#seteventmask)成員函式。 您可以使用[GetEventMask](reference/cricheditctrl-class.md#geteventmask)成員函式，抓取 rich edit 控制項的目前事件遮罩。

下列段落會列出數個特定的通知及其用途：

- EN_MSGFILTER 處理 EN_MSGFILTER 通知時，可讓類別（rich edit 控制項或其父視窗）篩選所有鍵盤和滑鼠輸入至控制項。 處理常式可以防止鍵盤或滑鼠訊息被處理，或藉由修改指定的[MSGFILTER](/windows/win32/api/richedit/ns-richedit-msgfilter)結構來變更訊息。

- EN_PROTECTED 處理 EN_PROTECTED 通知訊息，以偵測使用者何時嘗試修改受保護的文字。 若要將某個範圍的文字標示為受保護，您可以設定受保護的字元效果。 如需詳細資訊，請參閱[Rich Edit 控制項中的字元格式](character-formatting-in-rich-edit-controls.md)。

- EN_DROPFILES 您可以藉由處理 EN_DROPFILES 通知訊息，讓使用者能夠在 rich edit 控制項中放置檔案。 指定的[ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles)結構包含要卸載之檔案的相關資訊。

- EN_SELCHANGE 應用程式可以藉由處理 EN_SELCHANGE 通知訊息來偵測目前的選取範圍何時變更。 通知訊息會指定[SELCHANGE](/windows/win32/api/richedit/ns-richedit-selchange)結構，其中包含新選取專案的相關資訊。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控制項](controls-mfc.md)
