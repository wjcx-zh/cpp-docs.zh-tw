---
title: "COleDropTarget Class | Microsoft Docs"
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
  - "COleDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropTarget class"
  - "拖放, drop target"
  - "drop commands"
  - "drop commands, 接受"
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供在 Windows 和 OLE 程式庫之間的溝通機制。  
  
## 語法  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDropTarget::COleDropTarget](../Topic/COleDropTarget::COleDropTarget.md)|建構 `COleDropTarget` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md)|呼叫時，游標會先輸入視窗。|  
|[COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md)|呼叫，以便將游標拖曳到視窗之外。|  
|[COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md)|重複呼叫，當游標拖曳至視窗。|  
|[COleDropTarget::OnDragScroll](../Topic/COleDropTarget::OnDragScroll.md)|呼叫來決定游標是否拖曳至  視窗中捲動區域。|  
|[COleDropTarget::OnDrop](../Topic/COleDropTarget::OnDrop.md)|呼叫，將資料放入  視窗中，預設的處理常式。|  
|[COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md)|呼叫，將資料放入  視窗中，一開始的處理常式。|  
|[COleDropTarget::Register](../Topic/COleDropTarget::Register.md)|Windows 登錄為有效的置放目標。|  
|[COleDropTarget::Revoke](../Topic/COleDropTarget::Revoke.md)|讓視窗不再有效的置放目標。|  
  
## 備註  
 建立這個類別的物件允許 Windows 通過 OLE 拖放機制以接收資料。  
  
 若要取得視窗接受置放命令，您必須先建立 `COleDropTarget` 類別的物件，然後呼叫以指標的 [暫存器](../Topic/COleDropTarget::Register.md) 函式所需 `CWnd` 物件當做唯一的參數。  
  
 如需使用 OLE 拖放作業的詳細資訊，請參閱本文 [OLE 拖放 \(\)](../../mfc/drag-and-drop-ole.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDropSource Class](../../mfc/reference/coledropsource-class.md)