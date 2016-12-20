---
title: "CAutoHideDockSite Class | Microsoft Docs"
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
  - "CAutoHideDockSite"
  - "AllowShowOnPaneMenu"
  - "CAutoHideDockSite::AllowShowOnPaneMenu"
  - "CAutoHideDockSite.AllowShowOnPaneMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AllowShowOnPaneMenu method"
  - "CAutoHideDockSite class"
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: 32
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoHideDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CAutoHideDockSite` 可實作自動隱藏停駐窗格 [CDockSite Class](../../mfc/reference/cdocksite-class.md) 擴充。  
  
## 語法  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CAutoHideDockSite::CAutoHideDockSite`|建構 `CAutoHideDockSite` 物件。|  
|`CAutoHideDockSite::~CAutoHideDockSite`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指出是否在 `CAutoHideDockSite` 窗格會顯示 。|  
|[CAutoHideDockSite::CanAcceptPane](../Topic/CAutoHideDockSite::CanAcceptPane.md)|以判斷基底窗格物件是否 [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md)從衍生。|  
|[CAutoHideDockSite::DockPane](../Topic/CAutoHideDockSite::DockPane.md)|停駐窗格為這個 `CAuotHideDockSite` 物件。|  
|[CAutoHideDockSite::GetAlignRect](../Topic/CAutoHideDockSite::GetAlignRect.md)|擷取 Pin 站台的大小螢幕座標的。|  
|[CAutoHideDockSite::RepositionPanes](../Topic/CAutoHideDockSite::RepositionPanes.md)|重繪 `CAutoHideDockSite` 的窗格與全域框線和按鈕延伸。|  
|[CAutoHideDockSite::SetOffsetLeft](../Topic/CAutoHideDockSite::SetOffsetLeft.md)|在停駐列左邊設定邊界。|  
|[CAutoHideDockSite::SetOffsetRight](../Topic/CAutoHideDockSite::SetOffsetRight.md)|在停駐列右邊設定邊界。|  
|[CAutoHideDockSite::UnSetAutoHideMode](../Topic/CAutoHideDockSite::UnSetAutoHideMode.md)|對物件的呼叫 [CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md) 在 `CAutoHideDockSite`。|  
  
### 資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|[CAutoHideDockSite::m\_nExtraSpace](../Topic/CAutoHideDockSite::m_nExtraSpace.md)|定義空間的大小在工具列和停駐列邊緣之間。  這個間距從左邊緣或上邊緣測量，根據固定空間的對齊方式。|  
  
## 備註  
 當您呼叫 [CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md)時，架構會自動建立 `CAutoHideDockSite` 物件。  在許多情況下，您不需要直接使用或執行個體化這個類別。  
  
 停駐列是停駐窗格左邊和 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)左邊之間的間距。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## 範例  
 下列範例示範如何從物件擷取 `CMFCAutoHideBar``CAutoHideDockSite` 物件以及如何設定停駐列的左框線。  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/CPP/cautohidedocksite-class_1.cpp)]  
  
## 需求  
 **標題:** afxautohidedocksite.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)