---
title: "TOOLTIPTEXT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TOOLTIPTEXT
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: becbdcfcc6dbd26ae3095de098d12dbc078530cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tooltiptext-structure"></a>TOOLTIPTEXT 結構
撰寫您[工具提示通知處理常式](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，您必須使用`TOOLTIPTEXT`結構。 成員`TOOLTIPTEXT`結構：  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 `hdr`  
 識別需要文字的工具。 這個結構的成員中，您唯一需要的是控制項的命令 ID。 控制項的命令 ID 會是 `idFrom` 結構的 `NMHDR` 成員，可使用語法 `hdr.idFrom` 存取。 請參閱[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)成員的討論`NMHDR`結構。  
  
 `lpszText`  
 字串的位址，用於接收工具的文字。  
  
 `szText`  
 接收工具提示文字的緩衝區。 應用程式可以將文字複製到這個緩衝區而不用指定字串的位址。  
  
 `hinst`  
 執行個體的控制代碼，其中包含做為工具提示文字所使用的字串。 如果 `lpszText` 是工具提示文字的位址，則這個成員會是 NULL。  
  
 當您處理 `TTN_NEEDTEXT` 通知訊息時，請使用其中一種方法指定下列要顯示的字串：  
  
-   將文字複製到 `szText` 成員所指定的緩衝區。  
  
-   將包含文字的緩衝區位址複製至 `lpszText` 成員。  
  
-   將字串資源的識別項複製到 `lpszText` 成員，並將包含資源的執行個體控制代碼複製到 `hinst` 成員。  
  
## <a name="see-also"></a>請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

