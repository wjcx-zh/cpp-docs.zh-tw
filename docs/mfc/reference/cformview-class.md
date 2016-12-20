---
title: "CFormView Class | Microsoft Docs"
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
  - "CFormView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFormView class"
  - "form views"
  - "檢視, containing controls"
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFormView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於表單檢視的基底類別。  
  
## 語法  
  
```  
class CFormView : public CScrollView  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFormView::CFormView](../Topic/CFormView::CFormView.md)|建構 `CFormView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFormView::IsInitDlgCompleted](../Topic/CFormView::IsInitDlgCompleted.md)|用於初始化期間同步處理。|  
  
## 備註  
 表單檢視基本上是包含控制項的檢視。  這些控制項根據對話方塊範本資源而佈置。  如果您想要應用程式中有表單，請使用 `CFormView`。  這些檢視支援必要時使用 [CScrollView](../../mfc/reference/cscrollview-class.md) 功能來捲動。  
  
 如果您要[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)，您可以使用 `CFormView` 做為檢視類別的基礎，就能變成表單架構應用程式。  
  
 您也可以將新的[表單主題](../../mfc/form-views-mfc.md)插入到文件檢視架構的應用程式。  即使您的應用程式一開始不支援表單，Visual C\+\+ 也會在您插入新表單時加入這項支援。  
  
 MFC 應用程式精靈和 \[加入類別\] 命令是建立表單架構應用程式的慣用方法。  如果您需要建立表單架構應用程式，但不使用這些方法，請參閱[建立表單架構應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## 需求  
 **標頭：**afxext.h  
  
## 請參閱  
 [MFC 範例 SNAPVW](../../top/visual-cpp-samples.md)   
 [MFC 範例 VIEWEX](../../top/visual-cpp-samples.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CView::OnUpdate](../Topic/CView::OnUpdate.md)   
 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)   
 [CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)