---
title: "CStatic Class | Microsoft Docs"
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
  - "CStatic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "點陣圖, 顯示"
  - "控制項 [MFC], static"
  - "CStatic class"
  - "游標, 顯示"
  - "enhanced metafiles"
  - "enhanced metafiles, 顯示"
  - "圖示, 顯示"
  - "static controls"
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatic Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 靜態控制項的功能。  
  
## 語法  
  
```  
class CStatic : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStatic::CStatic](../Topic/CStatic::CStatic.md)|建構 `CStatic` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStatic::Create](../Topic/CStatic::Create.md)|建立視窗靜態控制項並將其附加至 `CStatic` 物件。|  
|[CStatic::DrawItem](../Topic/CStatic::DrawItem.md)|繪製主控描繪的靜態控制項的覆寫。|  
|[CStatic::GetBitmap](../Topic/CStatic::GetBitmap.md)|擷取點陣圖的控制代碼之前設定與 [SetBitmap](../Topic/CStatic::SetBitmap.md)。|  
|[CStatic::GetCursor](../Topic/CStatic::GetCursor.md)|擷取游標影像的控制代碼之前設定與 [SetCursor](../Topic/CStatic::SetCursor.md)。|  
|[CStatic::GetEnhMetaFile](../Topic/CStatic::GetEnhMetaFile.md)|擷取加強型中繼檔控制代碼之前設定與 [SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md)。|  
|[CStatic::GetIcon](../Topic/CStatic::GetIcon.md)|擷取圖示的控制代碼之前設定與 [SetIcon](../Topic/CStatic::SetIcon.md)。|  
|[CStatic::SetBitmap](../Topic/CStatic::SetBitmap.md)|指定在靜態控制項中顯示的點陣圖。|  
|[CStatic::SetCursor](../Topic/CStatic::SetCursor.md)|指定在靜態控制項中顯示的游標影像。|  
|[CStatic::SetEnhMetaFile](../Topic/CStatic::SetEnhMetaFile.md)|指定在靜態控制項中顯示的加強型中繼檔。|  
|[CStatic::SetIcon](../Topic/CStatic::SetIcon.md)|指定在靜態控制項顯示的圖示。|  
  
## 備註  
 靜態控制項顯示文字字串、方塊、矩形、圖示、游標、點陣圖、增強型中繼檔。  它可用來標記，將或分隔其他控制項容器。  靜態控制項通常不會使用輸入並不提供輸出，不過，如果，它會使用 **SS\_NOTIFY** 樣式，來通知它的滑鼠點選的父代。  
  
 使用兩個步驟的靜態控制項。  首先，請呼叫建構函式 `CStatic` 建構物件，然後呼叫 [建立](../Topic/CStatic::Create.md) 成員函式建立靜態控制項並將它附加至 `CStatic` 物件。  
  
 如果您在對話方塊內的 `CStatic` 物件 \(透過對話方塊資源\)，自動終結 `CStatic` 物件，在使用者關閉對話方塊時。  
  
 如果您在視窗內的 `CStatic` 物件，可能還需要終結它。  自動終結在視窗內的堆疊上建立的 `CStatic` 物件。  您可以使用 **new** 函式，建立。 `CStatic` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結它，當您完成使用後。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)