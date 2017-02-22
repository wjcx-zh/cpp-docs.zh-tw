---
title: "CMFCTasksPaneTaskGroup Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPaneTaskGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTaskGroup class"
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCTasksPaneTaskGroup Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTasksPaneTaskGroup` 類別是 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 控制項所使用的 Helper 類別。  型別 `CMFCTasksPaneTaskGroup` 物件表示工作群組。  工作群組是架構在另一個  方塊會顯示具有摺疊按鈕項目的清單。   方塊中可能有一個選擇性標頭 \(群組名稱\)。  如果群組摺疊，工作清單不是可見的。  
  
## 語法  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](../Topic/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup.md)|建構 `CMFCTasksPaneTaskGroup` 物件。|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::SetACCData](../Topic/CMFCTasksPaneTaskGroup::SetACCData.md)|判斷目前的工作群組的存取範圍的資料。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::m\_bIsBottom](../Topic/CMFCTasksPaneTaskGroup::m_bIsBottom.md)|判斷工作群組是否對齊工作窗格控制項的下方。|  
|[CMFCTasksPaneTaskGroup::m\_bIsCollapsed](../Topic/CMFCTasksPaneTaskGroup::m_bIsCollapsed.md)|判斷工作群組是否已摺疊。|  
|[CMFCTasksPaneTaskGroup::m\_bIsSpecial](../Topic/CMFCTasksPaneTaskGroup::m_bIsSpecial.md)|判斷工作群組是否為特殊名稱 *。*架構會以不同色彩顯示的特殊標頭。|  
|[CMFCTasksPaneTaskGroup::m\_lstTasks](../Topic/CMFCTasksPaneTaskGroup::m_lstTasks.md)|包含工作內部清單。|  
|[CMFCTasksPaneTaskGroup::m\_rect](../Topic/CMFCTasksPaneTaskGroup::m_rect.md)|指定群組標題的週框 \(Bounding Rectangle\)。|  
|[CMFCTasksPaneTaskGroup::m\_rectGroup](../Topic/CMFCTasksPaneTaskGroup::m_rectGroup.md)|指定群組的週框 \(Bounding Rectangle\)。|  
|[CMFCTasksPaneTaskGroup::m\_strName](../Topic/CMFCTasksPaneTaskGroup::m_strName.md)|指定群組名稱。|  
  
## 備註  
 下圖顯示已展開的工作群組:  
  
 ![展開的工作群組](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
 下圖顯示已摺疊的工作群組:  
  
 ![摺疊的工作群組](../Image/NextTaskGrpCollapse.png "NextTaskGrpCollapse")  
  
 下圖將顯示一個工作群組，不會將標題:  
  
 ![沒有標題的工作群組](../../mfc/reference/media/nexttaskgrpnocapt.png "NextTaskGrpNoCapt")  
  
 下圖顯示兩個工作群組。  第一個工作群組已標記為特殊可以將設定為 `TRUE`的 `m_bIsSpecial` 旗標，，而第二個工作群組不是特殊的。  請注意第一個工作群組的標頭如何小於第二個工作群組深:  
  
 ![特殊工作群組](../../mfc/reference/media/nexttaskgrpspecial.png "NextTaskGrpSpecial")  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## 需求  
 **標題:** afxTasksPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)