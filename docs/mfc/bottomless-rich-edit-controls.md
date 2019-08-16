---
title: 無底邊 Rich Edit 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
ms.openlocfilehash: 4affdbeed723ea83beda785116dc4c45771073b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509156"
---
# <a name="bottomless-rich-edit-controls"></a>無底邊 Rich Edit 控制項

您的應用程式可以視需要調整 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 的大小, 使其一律與內容相同。 Rich edit 控制項支援這種所謂的「無底邊」功能, 方法是在其內容的大小變更時, 傳送其父視窗的[EN_REQUESTRESIZE](/windows/win32/Controls/en-requestresize)通知訊息。

處理**EN_REQUESTRESIZE**通知訊息時, 應用程式應該將控制項的大小調整為所指定[REQRESIZE](/windows/win32/api/richedit/ns-richedit-reqresize)結構中的維度。 應用程式可能也會移動控制項附近的任何資訊，以配合控制項的高度變更。 若要調整控制項的大小, 您可以`CWnd`使用函式[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。

您可以使用[REQUESTRESIZE](../mfc/reference/cricheditctrl-class.md#requestresize)成員函式, 強制無底邊 rich edit 控制項傳送**EN_REQUESTRESIZE**通知訊息。 此訊息在[OnSize](../mfc/reference/cwnd-class.md#onsize)處理常式中可能會很有用。

若要接收**EN_REQUESTRESIZE**通知訊息, 您必須使用`SetEventMask`成員函式來啟用通知。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
