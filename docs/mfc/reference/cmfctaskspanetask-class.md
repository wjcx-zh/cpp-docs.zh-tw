---
title: "CMFCTasksPaneTask Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPaneTask"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTask class"
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCTasksPaneTask Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTasksPaneTask` 類別是表示工作窗格之控制項的 Helper 類別 \(\)[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)工作。  工作物件表示工作群組 \([CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)\) 的項目。  每個工作具有這個框架正在執行的命令，當使用者按一下工作與工作名稱左邊的圖示時。  
  
## 語法  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](../Topic/CMFCTasksPaneTask::CMFCTasksPaneTask.md)|建立及初始化 `CMFCTasksPaneTask` 物件。|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTask::SetACCData](../Topic/CMFCTasksPaneTask::SetACCData.md)|判斷網頁可及性資料為目前工作。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPaneTask::m\_bAutoDestroyWindow](../Topic/CMFCTasksPaneTask::m_bAutoDestroyWindow.md)|決定是否要自動終結工作視窗中。|  
|[CMFCTasksPaneTask::m\_bIsBold](../Topic/CMFCTasksPaneTask::m_bIsBold.md)|判斷這個框架是否以粗體文字的工作標籤。|  
|[CMFCTasksPaneTask::m\_dwUserData](../Topic/CMFCTasksPaneTask::m_dwUserData.md)|包含這個框架與工作相關聯的使用者定義的資料。  如果工作沒有關聯的資料，設定為零。|  
|[CMFCTasksPaneTask::m\_hwndTask](../Topic/CMFCTasksPaneTask::m_hwndTask.md)|將控制代碼傳遞至工作。|  
|[CMFCTasksPaneTask::m\_nIcon](../Topic/CMFCTasksPaneTask::m_nIcon.md)|在架構中工作旁邊顯示影像的影像清單的索引。|  
|[CMFCTasksPaneTask::m\_nWindowHeight](../Topic/CMFCTasksPaneTask::m_nWindowHeight.md)|工作視窗的高度。  如果工作沒有工作視窗中，這個值是零。|  
|[CMFCTasksPaneTask::m\_pGroup](../Topic/CMFCTasksPaneTask::m_pGroup.md)|為 `CMFCTasksPaneTaskGroup` 的指標屬於這項工作。|  
|[CMFCTasksPaneTask::m\_rect](../Topic/CMFCTasksPaneTask::m_rect.md)|指定工作的週框 \(Bounding Rectangle\)。|  
|[CMFCTasksPaneTask::m\_strName](../Topic/CMFCTasksPaneTask::m_strName.md)|工作的名稱。|  
|[CMFCTasksPaneTask::m\_uiCommandID](../Topic/CMFCTasksPaneTask::m_uiCommandID.md)|指定架構執行命令的命令 ID，當使用者按一下工作時。  如果這個值不是有效的命令 ID，工作會將簡單的標籤。|  
  
## 備註  
 下圖顯示包含三項工作的一個工作群組:  
  
 ![展開的工作群組](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
> [!NOTE]
>  如果工作沒有有效的命令 ID，則會將其視為簡單的標籤。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## 需求  
 **標題:** afxTasksPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)