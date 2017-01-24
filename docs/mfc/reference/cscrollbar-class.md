---
title: "CScrollBar Class | Microsoft Docs"
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
  - "CScrollBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [MFC], 捲軸"
  - "CScrollBar class"
  - "捲軸"
  - "SCROLLBAR window class"
  - "Windows common controls [C++], CScrollBar"
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CScrollBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供視窗捲軸控制項的功能。  
  
## 語法  
  
```  
class CScrollBar : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CScrollBar::CScrollBar](../Topic/CScrollBar::CScrollBar.md)|建構 `CScrollBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CScrollBar::Create](../Topic/CScrollBar::Create.md)|建立視窗捲軸並將其附加至 `CScrollBar` 物件。|  
|[CScrollBar::EnableScrollBar](../Topic/CScrollBar::EnableScrollBar.md)|啟用或停用捲軸的一或兩個箭號。|  
|[CScrollBar::GetScrollBarInfo](../Topic/CScrollBar::GetScrollBarInfo.md)|使用 `SCROLLBARINFO` 結構，擷取與捲軸的相關資訊。|  
|[CScrollBar::GetScrollInfo](../Topic/CScrollBar::GetScrollInfo.md)|擷取有關捲軸的相關資訊。|  
|[CScrollBar::GetScrollLimit](../Topic/CScrollBar::GetScrollLimit.md)|擷取捲軸的限制。|  
|[CScrollBar::GetScrollPos](../Topic/CScrollBar::GetScrollPos.md)|擷取捲動方塊的目前位置。|  
|[CScrollBar::GetScrollRange](../Topic/CScrollBar::GetScrollRange.md)|擷取指定捲軸的目前最小和最大捲軸位置。|  
|[CScrollBar::SetScrollInfo](../Topic/CScrollBar::SetScrollInfo.md)|如需設定捲軸的相關資訊。|  
|[CScrollBar::SetScrollPos](../Topic/CScrollBar::SetScrollPos.md)|設定捲動方塊的目前位置。|  
|[CScrollBar::SetScrollRange](../Topic/CScrollBar::SetScrollRange.md)|設定指定捲軸的最小和最大位置值。|  
|[CScrollBar::ShowScrollBar](../Topic/CScrollBar::ShowScrollBar.md)|顯示或隱藏每個捲軸。|  
  
## 備註  
 您使用兩個步驟的捲軸控制項。  首先，請呼叫建構函式 `CScrollBar``CScrollBar` 建構物件，然後呼叫 [建立](../Topic/CScrollBar::Create.md) 成員函式建立視窗捲軸控制項並將它附加至 `CScrollBar` 物件。  
  
 如果您在對話方塊內的 `CScrollBar` 物件 \(透過對話方塊資源\)，自動終結 `CScrollBar` ，當使用者關閉對話方塊時。  
  
 如果您在視窗內的 `CScrollBar` 物件，可能還需要終結它。  
  
 如果您在堆疊上建立物件， `CScrollBar` 自動終結。  您可以使用 **new** 函式，建立。 `CScrollBar` 堆積中的物件，您必須呼叫物件上的 **刪除** 終結此物件，在使用者結束視窗捲軸時。  
  
 如果您在 `CScrollBar` 配置物件的任何記憶體，請覆寫 `CScrollBar` 解構函式處理組態。  
  
 如需使用 `CScrollBar`的相關資訊，請參閱 [控制項](../../mfc/controls-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
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
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)