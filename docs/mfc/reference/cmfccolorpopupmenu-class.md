---
title: "CMFCColorPopupMenu Class | Microsoft Docs"
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
  - "CMFCColorPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPopupMenu class"
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示使用者利用選取在文件或應用程式之色彩的快顯功能表。  
  
## 語法  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](../Topic/CMFCColorPopupMenu::CMFCColorPopupMenu.md)|建構 `CMFCColorPopupMenu` 物件。|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCColorPopupMenu::CreateTearOffBar](../Topic/CMFCColorPopupMenu::CreateTearOffBar.md)|建立可停駐到 Tear\-Off 色軸。  \(覆寫 [CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md)\)。|  
|[CMFCColorPopupMenu::GetMenuBar](../Topic/CMFCColorPopupMenu::GetMenuBar.md)|傳回內嵌在快顯功能表內的 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 。  \(覆寫 [CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md)\)。|  
|`CMFCColorPopupMenu::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCColorPopupMenu::SetPropList](../Topic/CMFCColorPopupMenu::SetPropList.md)|設定 `CMFCColorBar` 內嵌物件的屬性方格控制項物件。|  
  
### 資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`m_bEnabledInCustomizeMode`|判斷是否要顯示為色軸的布林值。|  
|`m_wndColorBar`|提供色彩選取的 `CMFCColorBar` 物件。|  
  
### 備註  
 繼承自這個類別 `CMFCPopupMenu` 類別的快顯功能表功能和處理提供色彩選取的 `CMFCColorBar` 物件。  當工具列框架是自訂模式，而且 `m_bEnabledInCustomizeMode` 成員設定為，則 `FALSE`色軸物件不會顯示。  如需自訂模式的詳細資訊，請參閱 [CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)  
  
 如需 `CMFCColorBar` 的詳細資訊，請參閱 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## 需求  
 **標題:** afxcolorpopupmenu.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)