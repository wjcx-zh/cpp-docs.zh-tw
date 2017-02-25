---
title: "COleDropSource Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDropSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropSource class"
  - "拖放, drop source"
  - "拖曳作業"
  - "drop target, dragging data to"
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleDropSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許資料拖曳到置放目標。  
  
## 語法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDropSource::COleDropSource](../Topic/COleDropSource::COleDropSource.md)|建構 `COleDropSource` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDropSource::GiveFeedback](../Topic/COleDropSource::GiveFeedback.md)|在拖放作業期間變更游標。|  
|[COleDropSource::OnBeginDrag](../Topic/COleDropSource::OnBeginDrag.md)|控制代碼滑鼠捕捉在拖放作業時。|  
|[COleDropSource::QueryContinueDrag](../Topic/COleDropSource::QueryContinueDrag.md)|檢查拖曳是否應該繼續。|  
  
## 備註  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md) 類別處理拖放作業的接收的部分。  `COleDropSource` 物件決定拖放作業啟動時，提供回應在拖曳作業期間和判斷負責，在拖曳作業結束時。  
  
 若要使用 `COleDropSource` 物件，請呼叫建構函式。  這會簡化程序決定使用 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)、 [COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)或 [COleServerItem::DoDragDrop](../Topic/COleServerItem::DoDragDrop.md) 函式，哪些事件，例如滑鼠點選，開始拖曳作業。  這些函式會為您建立 `COleDropSource` 物件。  您可能會想要修改 `COleDropSource` 可覆寫的函式的預設行為。  這些成員函式會呼叫在適當的時間由架構。  
  
 如需使用 OLE 拖放作業的詳細資訊，請參閱本文 [OLE 拖放 \(\)](../../mfc/drag-and-drop-ole.md)。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)