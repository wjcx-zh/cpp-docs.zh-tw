---
title: "CMFCDropDownFrame Class | Microsoft Docs"
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
  - "CMFCDropDownFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownFrame class"
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDropDownFrame Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供下拉式框架視窗功能提供下拉式工具列和工具列上的下拉式按鈕。  
  
## 語法  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|預設建構函式。|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDropDownFrame::Create](../Topic/CMFCDropDownFrame::Create.md)|建立 `CMFCDropDownFrame` 物件。|  
|`CMFCDropDownFrame::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCDropDownFrame::GetParentMenuBar](../Topic/CMFCDropDownFrame::GetParentMenuBar.md)|擷取下拉式父框架的功能表列。|  
|[CMFCDropDownFrame::GetParentPopupMenu](../Topic/CMFCDropDownFrame::GetParentPopupMenu.md)|擷取下拉式父框架的快顯功能表。|  
|`CMFCDropDownFrame::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCDropDownFrame::RecalcLayout](../Topic/CMFCDropDownFrame::RecalcLayout.md)|重新調整位置的框架。|  
|[CMFCDropDownFrame::SetAutoDestroy](../Topic/CMFCDropDownFrame::SetAutoDestroy.md)|設定是否會自動毀棄子工具列上的下拉式視窗。|  
  
### 備註  
 這個類別並不適合直接從您的程式碼使用。  
  
 架構會使用這個類別會提供架構行為。 `CMFCDropDownToolbar` 和 `CMFCDropDownToolbarButton` 類別。  如需這些類別的詳細資訊，請參閱[CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)和 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。  
  
## 範例  
 下列範例示範如何擷取指標 `CMFCDropDownFrame` 物件從 `CFrameWnd` 類別以及如何設定會自動終結的子工具列上的下拉式視窗。  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/CPP/cmfcdropdownframe-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## 需求  
 **標題:** afxdropdowntoolbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)