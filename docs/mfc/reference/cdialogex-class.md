---
title: "CDialogEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogEx class"
  - "CDialogEx::PreTranslateMessage method"
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDialogEx` 類別會指定對話方塊的背景影像和背景色彩。  
  
## 語法  
  
```  
class CDialogEx : public CDialog  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDialogEx::CDialogEx](../Topic/CDialogEx::CDialogEx.md)|建構 `CDialogEx` 物件。|  
|`CDialogEx::~CDialogEx`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDialogEx::SetBackgroundColor](../Topic/CDialogEx::SetBackgroundColor.md)|設定對話方塊的背景色彩。|  
|[CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md)|設定對話方塊的背景影像。|  
  
## 備註  
 若要使用 `CDialogEx` 類別，請將您的對話方塊類別從 `CDialogEx` 類別進行衍生，而不是從 `CDialog` 類別。  
  
 對話方塊影像會儲存在資源檔中。  架構會自動刪除從資源檔載入的任何影像。  若要以程式設計方式刪除目前的背景影像，請呼叫 [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md) 方法或實作 `OnDestroy` 事件處理常式。  當您呼叫 [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md) 方法時，請傳入 `HBITMAP` 參數做為影像控制代碼。  `CDialogEx` 物件會取得影像的擁有權，而若 `m_bAutoDestroyBmp` 旗標是 `TRUE` 的話，則會將它刪除。  
  
 `CDialogEx` 物件可以是 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 物件的父物件。  當 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 物件開啟時，[CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 物件會呼叫 `CDialogEx::SetActiveMenu` 方法。  之後，`CDialogEx` 物件會處理任何功能表事件，直到 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 物件關閉。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## 需求  
 **標頭：** afxdialogex.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)