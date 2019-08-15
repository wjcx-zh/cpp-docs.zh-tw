---
title: TOOLTIPTEXT 結構
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 80b95225a277a7985c30e5ea453597b06e501753
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513295"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 結構

撰寫[工具提示通知處理常式](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)時, 您必須使用**TOOLTIPTEXT**結構。 **TOOLTIPTEXT**結構的成員如下:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*hdr*<br/>
識別需要文字的工具。 這個結構的成員中，您唯一需要的是控制項的命令 ID。 控制項的命令識別碼會在**NMHDR**結構`hdr.idFrom`的*idFrom*成員中, 並使用語法來存取。 如需**NMHDR**結構成員的討論, 請參閱[NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) 。

*lpszText*<br/>
字串的位址，用於接收工具的文字。

*szText*<br/>
接收工具提示文字的緩衝區。 應用程式可以將文字複製到這個緩衝區而不用指定字串的位址。

*hinst*<br/>
執行個體的控制代碼，其中包含做為工具提示文字所使用的字串。 如果*lpszText*是工具提示文字的位址, 這個成員就是 Null。

當您處理 `TTN_NEEDTEXT` 通知訊息時，請使用其中一種方法指定下列要顯示的字串：

- 將文字複製到*szText*成員所指定的緩衝區。

- 將包含文字的緩衝區位址複製到*lpszText*成員。

- 將字串資源的識別碼複製到*lpszText*成員, 並將包含該資源的實例之控制碼複製到*hinst*成員。

## <a name="see-also"></a>另請參閱

[非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
