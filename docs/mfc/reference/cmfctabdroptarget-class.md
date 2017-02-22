---
title: "CMFCTabDropTarget Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabDropTarget class"
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCTabDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供在索引標籤控制項和 OLE 程式庫之間的溝通機制。  
  
## 語法  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|預設建構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCTabDropTarget::OnDragEnter](../Topic/CMFCTabDropTarget::OnDragEnter.md)|呼叫框架，則當使用者拖曳物件插入索引標籤視窗。  \(覆寫 [COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md)\)。|  
|[CMFCTabDropTarget::OnDragLeave](../Topic/CMFCTabDropTarget::OnDragLeave.md)|呼叫框架，則當使用者拖曳物件擁有焦點的視窗索引標籤之外。  \(覆寫 [COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md)\)。|  
|[CMFCTabDropTarget::OnDragOver](../Topic/CMFCTabDropTarget::OnDragOver.md)|呼叫框架，則當使用者拖曳擁有焦點的視窗索引標籤上的物件。  \(覆寫 [COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md)\)。|  
|[CMFCTabDropTarget::OnDropEx](../Topic/CMFCTabDropTarget::OnDropEx.md)|呼叫框架，而使用者釋放滑鼠按鈕拖曳作業結束時。  \(覆寫 [COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md)\)。|  
|[CMFCTabDropTarget::Register](../Topic/CMFCTabDropTarget::Register.md)|將控制項註冊為可以是 OLE 拖放作業的目標之一。|  
  
### 備註  
 這個類別會提供拖放支援將 `CMFCBaseTabCtrl` 類別。  如果您的應用程式初始化使用 [AfxOleInit](../Topic/AfxOleInit.md) 的 OLE 程式庫提供拖放作業的作用， `CMFCBaseTabCtrl` 物件註冊。  
  
 `CMFCTabDropTarget` 類別將游標下方的  索引標籤來擴充基底類別，在拖曳作業時發生作用中時。  如需拖放作業的詳細資訊，請參閱 [OLE 拖放 \(\)](../../mfc/drag-and-drop-ole.md)。  
  
## 範例  
 下列範例示範如何建構 `CMFCTabDropTarget` 物件並使用其 `Register` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/CPP/cmfctabdroptarget-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## 需求  
 **標題:** afxbasetabctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [OLE 拖放 \(\)](../../mfc/drag-and-drop-ole.md)