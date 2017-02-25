---
title: "CCtrlView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCtrlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCtrlView class"
  - "控制項 [MFC], common"
  - "檢視, and common controls"
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CCtrlView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符合文件檢視架構 Windows 98 和 Windows NT 版本所支援的通用控制項 3.51 \(含\) 以後版本。  
  
## 語法  
  
```  
class CCtrlView : public CView  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCtrlView::CCtrlView](../Topic/CCtrlView::CCtrlView.md)|建構 `CCtrlView` 物件。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CCtrlView::OnDraw](../Topic/CCtrlView::OnDraw.md)|使用指定的裝置內容，會由架構所繪製。|  
|[CCtrlView::PreCreateWindow](../Topic/CCtrlView::PreCreateWindow.md)|會在視窗視窗的建立之前附加至這個 `CCtrlView` 物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCtrlView::m\_dwDefaultStyle](../Topic/CCtrlView::m_dwDefaultStyle.md)|包含檢視類別的預設樣式。|  
|[CCtrlView::m\_strClass](../Topic/CCtrlView::m_strClass.md)|包含視窗類別名稱檢視類別。|  
  
## 備註  
 類別 `CCtrlView` 及其衍生類別， [CEditView](../../mfc/reference/ceditview-class.md)、 [CListView](../../mfc/reference/clistview-class.md)、 [CTreeView](../../mfc/reference/ctreeview-class.md)和 [CRichEditView](../../mfc/reference/cricheditview-class.md)，符合文件檢視架構\/98 Windows 95 和 Windows NT 版本所支援的新 Controls 3.51 \(含\) 以後版本。  如需檢視文件結構的詳細資訊，請參閱 [文件\/檢視架構](../../mfc/document-view-architecture.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CView Class](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CTreeView Class](../../mfc/reference/ctreeview-class.md)   
 [CListView Class](../../mfc/reference/clistview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)