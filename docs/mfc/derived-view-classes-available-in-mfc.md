---
title: "MFC 中的可用衍生檢視類別 | Microsoft Docs"
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
  - "CView 類別, 類別衍生自"
  - "衍生類別, 檢視類別"
  - "檢視類別, 衍生"
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 中的可用衍生檢視類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示 MFC 的檢視類別和關聯性的相鄰。  檢視類別的功能取決於其所衍生的 MFC 檢視類別。  
  
### 檢視類別。  
  
|類別|說明|  
|--------|--------|  
|[CView](../mfc/reference/cview-class.md)|所有檢視的基底類別。|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|`CTreeView`、 `CListView`、 `CEditView`和 `CRichEditView`基底類別。  這些類別可讓您使用與所指定之 Windows 通用控制項的文件\/檢視架構。|  
|[CEditView](../mfc/reference/ceditview-class.md)|根據視窗編輯方塊控制項的簡單的檢視。  允許輸入和編輯文字，並且可以使用做為的基礎為簡單的文字編輯器應用程式。  請參閱`CRichEditView`。|  
|[CRichEditView](../mfc/reference/cricheditview-class.md)|包含 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 物件的檢視。  這個類別是與 `CEditView`類似，不過，不同於 `CEditView`， `CRichEditView` 控制代碼。|  
|[CListView](../mfc/reference/clistview-class.md)|包含 [CListCtrl](../mfc/reference/clistctrl-class.md) 物件的檢視。|  
|[CTreeView](../mfc/reference/ctreeview-class.md)|包含 [CTreeCtrl](../mfc/reference/ctreectrl-class.md) 物件，類似於 Visual C\+\+ 的方案總管視窗中檢視的檢視。|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|`CFormView`、 `CRecordView`和 `CDaoRecordView`基底類別。  捲動檢視內容的實作。|  
|[CFormView](../mfc/reference/cformview-class.md)|表單檢視，該檢視包含控制項。  表單架構應用程式的一個或多個這類表單介面。|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|應用程式的使用者可以瀏覽 World Wide Web 網站的 Web 瀏覽器檢視，以及資料夾在檔案系統和 Web。  Web 瀏覽器檢視也可主動式文件容器。|  
|[CRecordView](../mfc/reference/crecordview-class.md)|顯示在控制項的 ODBC 資料庫資料錄的表單檢視。  如果您在專案的 ODBC 支援，檢視的基底類別是 `CRecordView`。  這個檢視連接到 `CRowset` 物件。|  
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|顯示在控制項的 DAO 資料庫資料錄的表單檢視。  如果您在專案的 DAO 支援，檢視的基底類別是 `CDaoRecordView`。  這個檢視連接到 `CDaoRecordset` 物件。|  
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|在控制項中顯示 OLE DB 資料錄的表單檢視。  如果您選擇在專案中的 OLE DB 支援，檢視的基底類別是 `COleDBRecordView`。  這個檢視連接到 `CRowset` 物件。|  
  
> [!NOTE]
>  根據 MFC 4.0 版， `CEditView` 衍生自 `CCtrlView`。  
  
 若要使用這些類別在應用程式中，從它們衍生應用程式的檢視類別。  如需相關資訊，請參閱 [捲動和縮放檢視](../mfc/scrolling-and-scaling-views.md)。  如需資料庫類別的詳細資訊，請參閱 [概觀:資料庫程式設計](../data/data-access-programming-mfc-atl.md)。  
  
## 請參閱  
 [使用檢視](../mfc/using-views.md)