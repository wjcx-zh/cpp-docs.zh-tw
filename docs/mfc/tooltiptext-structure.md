---
title: "TOOLTIPTEXT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TOOLTIPTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "工具提示 [C++], 告知"
  - "TOOLTIPTEXT 結構"
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TOOLTIPTEXT 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

撰寫 [工具提示告知處理常式。](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)，您必須使用 `TOOLTIPTEXT` 結構。  `TOOLTIPTEXT`結構的成員包括:  
  
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
 識別需要文字的工具。  您可能需要將這個結構的成員是控制命令 ID.  控制命令 ID 在 `NMHDR` 結構的 `idFrom` 成員，可存取使用語法 `hdr.idFrom`。  如需 `NMHDR` 結構成員的討論參閱 [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) 。  
  
 `lpszText`  
 接收工具的文字字串的位址。  
  
 `szText`  
 緩衝區的工具提示文字。  應用程式可以將文字複製到這個緩衝區而不用指定字串的位址。  
  
 `hinst`  
 包含做為工具提示文字所使用的字串執行個體的控制代碼。  如果 `lpszText` 是工具提示文字的位址，這個成員是空的。  
  
 當您處理 `TTN_NEEDTEXT` 通知訊息時，請指定下列其中一種方法將顯示的字串:  
  
-   將文字複製到 `szText` 成員所指定的緩衝區。  
  
-   複製包含文字至 `lpszText` 成員緩衝區的位址。  
  
-   複製字串資源的識別項給 `lpszText` 成員，並複製包含資源給 `hinst` 成員的執行個體控制代碼。  
  
## 請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)