---
title: "CTabView Class | Microsoft Docs"
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
  - "CTabView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabView class"
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CTabView` 類別會簡化使用索引標籤控制項類別 \([CMFCTabCtrl](../../mfc/reference/ctabview-class.md)\) 在使用 MFC 的文件\/檢視架構的應用程式。  
  
## 語法  
  
```  
class CTabbedView : public CView  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTabView::AddView](../Topic/CTabView::AddView.md)|加入新的檢視加入至索引標籤控制項。|  
|[CTabView::FindTab](../Topic/CTabView::FindTab.md)|傳回指定的檢視表上的索引標籤控制項。|  
|[CTabView::GetActiveView](../Topic/CTabView::GetActiveView.md)|傳回指向目前作用中檢視|  
|[CTabView::GetTabControl](../Topic/CTabView::GetTabControl.md)|傳回至索引標籤控制項的參考與這個檢視。|  
|[CTabView::RemoveView](../Topic/CTabView::RemoveView.md)|從的索引標籤控制項中移除這個檢視。|  
|[CTabView::SetActiveView](../Topic/CTabView::SetActiveView.md)|將檢視中。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CTabView::IsScrollBar](../Topic/CTabView::IsScrollBar.md)|呼叫框架，當建立選項檢視判斷索引標籤時檢視是否具有共用水平捲軸。|  
|[CTabView::OnActivateView](../Topic/CTabView::OnActivateView.md)|呼叫框架，該索引標籤上的  檢視可讓使用中或非作用中。|  
  
## 備註  
 這個類別可讓您輕鬆地將一個索引標籤式檢視文件\/檢視應用程式。  `CTabView` 是 `CView`\-包含內嵌 `CMFCTabCtrl` 物件的衍生類別。  `CTabView` 處理要求的所有訊息 `CMFCTabCtrl` 支援物件。  從 `CTabView` 衍生類別並將它貼到應用程式，然後將 `CView`\-使用 `AddView` 方法的衍生類別。  索引標籤控制項會顯示這些  索引標籤。  
  
 例如，您可能有一個可以用不同的方式來表示的文件中:當做報表，圖表，可編輯的表單，依此類推。  您可以建立繪製資料的個別檢視視需要，將它們插入至您的 `CTabView`衍生物件並以索引標籤形式，而不需要其他程式碼。  
  
 [TabbedView 範例:MFC 索引標籤式檢視應用程式](../../top/visual-cpp-samples.md) 說明 `CTabView`用法。  
  
## 範例  
 下列範例顯示如何在 `CTabView` TabbedView 範例。  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/CPP/ctabview-class_1.h)]  
  
## 需求  
 **標題:** afxTabView.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTabView Class](../../mfc/reference/ctabview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)