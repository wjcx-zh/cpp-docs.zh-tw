---
title: "CDragListBox Class | Microsoft Docs"
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
  - "CDragListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDragListBox class"
  - "drag list box [C++]"
  - "dragging list items"
  - "清單方塊"
  - "Windows [C++], 清單方塊"
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDragListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除了提供視窗清單方塊的功能， `CDragListBox` 類別允許使用者捲動清單方塊項目，例如檔案名稱，在清單方塊中。  
  
## 語法  
  
```  
class CDragListBox : public CListBox  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDragListBox::CDragListBox](../Topic/CDragListBox::CDragListBox.md)|建構 `CDragListBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDragListBox::BeginDrag](../Topic/CDragListBox::BeginDrag.md)|呼叫由架構，在拖曳作業開始。|  
|[CDragListBox::CancelDrag](../Topic/CDragListBox::CancelDrag.md)|呼叫框架，則會取消拖曳作業。|  
|[CDragListBox::Dragging](../Topic/CDragListBox::Dragging.md)|呼叫框架拖曳作業時。|  
|[CDragListBox::DrawInsert](../Topic/CDragListBox::DrawInsert.md)|繪製拖曳清單方塊插入的方針。|  
|[CDragListBox::Dropped](../Topic/CDragListBox::Dropped.md)|呼叫框架中，項目會卸除之後。|  
|[CDragListBox::ItemFromPt](../Topic/CDragListBox::ItemFromPt.md)|傳回被拖曳項目的座標。|  
  
## 備註  
 清單方塊中提供這項功能可讓使用者排序清單中的項目會以任何方式最有用的設定。  根據預設，清單方塊會移至項目清單的新位置。  不過， `CDragListBox` 物件可以自訂複製項目而不移除它們。  
  
 清單方塊控制項與 `CDragListBox` 類別不可以有 **LBS\_SORT** 或 **LBS\_MULTIPLESELECT** 樣式。  如需清單方塊樣式的描述，請參閱 [清單方塊的樣式。](../../mfc/reference/list-box-styles.md)。  
  
 若要使用拖曳清單方塊中的現有對話方塊應用程式，請將清單方塊控制項加入至對話方塊樣板使用對話方塊編輯器並將成員變數 \(分類 `Control` 和變數型別 `CDragListBox`\) 與您的對話方塊樣板的清單方塊控制項的。  
  
 如需將控制項的詳細資訊給成員變數，請參閱 [用於定義對話方塊控制項的成員變數捷徑](../../mfc/defining-member-variables-for-dialog-controls.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC TSTCON 範例](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)