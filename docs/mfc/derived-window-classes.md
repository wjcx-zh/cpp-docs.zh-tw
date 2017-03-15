---
title: "衍生的視窗類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], 衍生"
  - "CWnd 類別, 類別衍生自"
  - "衍生類別, 視窗類別"
  - "階層, 視窗類別"
  - "視窗類別階層"
  - "視窗類別, 衍生"
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 衍生的視窗類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以直接從 [CWnd](../mfc/reference/cwnd-class.md) 建立視窗，或從 `CWnd` 衍生新的視窗類別。  這通常會是建立自訂視窗的方法。  不過，大部分用於架構計劃的視窗是從 `CWnd` 衍生的框架視窗類別其中之一所建立，其為 MFC 所提供。  
  
## 框架視窗類別  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 用作 SDI 框架視窗，建構單一文件及其檢視。  框架視窗是應用程式的主框架視窗和目前文件的框架視窗。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 用作 MDI 應用程式的主框架視窗。  主框架視窗是所有 MDI 文件視窗的容器並共享其功能表列。  MDI 框架視窗是出現在桌面最上層視窗。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 用作開啟在 MDI 主框架視窗中的個別文件。  每個文件及其檢視由 MDI 主框架視窗內包含的 MDI 子框架視窗框架所建構。  MDI 子視窗的外觀很像一般的框架視窗，但它是包含在 MDI 框架視窗內而非桌面上。  然而， MDI 子視窗缺少功能表列，所以必須和包含功能表列的 MDI 框架視窗共享。  
  
 如需詳細資訊，請參閱 [框架視窗](../mfc/frame-windows.md)。  
  
## 從 CWnd 衍生的其他視窗類別  
 除了框架視窗以外，其他幾個視窗的主要類別衍生自 `CWnd`：  
  
 *檢視*  
 檢視是使用 `CWnd`衍生類別 [CView](../mfc/reference/cview-class.md) \(或它的衍生類別\) 所建立。  檢視會附加到文件並做為文件和使用者之間的媒介。  檢視是一個子視窗 \(非 MDI 子系\) ，通常會填滿 SDI 框架視窗的工作區或 MDI 子框架視窗 \(或工具列和狀態列未涵蓋的工作區部分\)。  
  
 *對話方塊*  
 對話方塊是使用 `CWnd` 衍生類別 [CDialog](../mfc/reference/cdialog-class.md) 來建立。  
  
 *表單*  
 以對話方塊樣板資源為基礎的表格檢視（例如對話方塊）是使用類別 [CFormView](../mfc/reference/cformview-class.md)、 [CRecordView](../mfc/reference/crecordview-class.md) 或 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 建立。  
  
 *控制項*  
 控制項 \(例如按鈕、清單方塊和下拉式方塊\) 會使用衍生自 `CWnd` 的其他類別來建立。  請參閱 [控制項主題](../mfc/controls-mfc.md)。  
  
 *控制列*  
 包含控制項的子視窗。  範例包含工具列和狀態列。  請參閱 [控制列](../mfc/control-bars.md)。  
  
## 視窗類別階層  
 請參閱 *《 MFC 參考》中的*[MFC 階層架構圖表](../mfc/hierarchy-chart.md) 。  「檢視」的說明在 [文件\/檢視架構](../mfc/document-view-architecture.md)。  對話方塊的說明在 [對話方塊](../mfc/dialog-boxes.md)。  
  
## 建置特殊目的的視窗類別  
 除了類別庫所提供的視窗類別之外，您可能需要特殊目的的子視窗。  要建立這種視窗，請建立您的 [CWnd](../mfc/reference/cwnd-class.md) 衍生類別並將它設為框架或檢視的子視窗。  記住框架處理的範圍是文件框架視窗的工作區。  大部分的工作區由檢視處理，不過其他視窗（例如控制列或自訂視窗）可能與檢視共用空間。  要在框架視窗的工作區內調整子視窗的位置，您可能需要和 [CView](../mfc/reference/cview-class.md) 及 [CControlBar](../mfc/reference/ccontrolbar-class.md) 類別中的機制互動。  
  
 [建立視窗](../mfc/creating-windows.md) 討論建立視窗物件及其管理的視窗。  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)