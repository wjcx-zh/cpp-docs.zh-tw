---
title: TOOLTIPTEXT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c06b98acec18e845fd1353875c1453c4bee8b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097155"
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 結構
撰寫您[工具提示通知處理常式](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，您必須使用**TOOLTIPTEXT**結構。 成員**TOOLTIPTEXT**結構：  
  
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
  
 *hdr*  
 識別需要文字的工具。 這個結構的成員中，您唯一需要的是控制項的命令 ID。 控制項的命令 ID 會處於*idFrom*隸屬**NMHDR**語法存取結構`hdr.idFrom`。 請參閱[NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr)如需成員的討論**NMHDR**結構。  
  
 *lpszText*  
 字串的位址，用於接收工具的文字。  
  
 *szText*  
 接收工具提示文字的緩衝區。 應用程式可以將文字複製到這個緩衝區而不用指定字串的位址。  
  
 *hinst*  
 執行個體的控制代碼，其中包含做為工具提示文字所使用的字串。 如果*lpszText*是位址的工具提示文字，這個成員為 NULL。  
  
當您處理 `TTN_NEEDTEXT` 通知訊息時，請使用其中一種方法指定下列要顯示的字串：  
  
-   將文字複製到所指定的緩衝區*szText*成員。  
  
-   包含所要的文字的緩衝區位址複製*lpszText*成員。  
  
-   複製到字串資源的識別項*lpszText*成員，然後複製包含資源的執行個體的控制代碼*hinst*成員。  
  
## <a name="see-also"></a>另請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

