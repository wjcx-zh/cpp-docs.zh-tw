---
title: "CMFCWindowsManagerDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCWindowsManagerDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCWindowsManagerDialog class"
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCWindowsManagerDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCWindowsManagerDialog` 物件可讓使用者管理在 MDI 應用程式的子視窗。  
  
## 語法  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](../Topic/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog.md)|建構 `CMFCWindowsManagerDialog` 物件。|  
  
## 備註  
 `CMFCWindowsManagerDialog` 包含 MDI 已經在應用程式的子視窗清單。  您可以使用這個對話方塊，使用者可以手動控制項的 MDI 子視窗的狀態。  
  
 `CMFCWindowsManagerDialog` 內嵌在 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)內。  `CMFCWindowsManagerDialog` 不是您應該手動建立的類別。  相反地，請呼叫函式， [CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)，它會建立並顯示 `CMFCWindowsManagerDialog` 物件。  
  
## 範例  
 下列範例示範如何透過呼叫 `CMDIFrameWndEx::ShowWindowsDialog``CMFCWindowsManagerDialog` 建構物件。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/CPP/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## 需求  
 **標題:** afxWindowsManagerDialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)   
 [CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)