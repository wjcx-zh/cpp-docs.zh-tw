---
title: "CDaoRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式精靈 [C++], creating record views"
  - "繫結控制項 [C++], displaying database data"
  - "CDaoRecordView 類別"
  - "控制項 [MFC], 資料繫結"
  - "資料繫結 [C++], DAO views"
  - "資料繫結控制項 [C++], DAO 控制項"
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDaoRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在控制項中顯示資料庫資料錄的檢視。  
  
## 語法  
  
```  
  
class AFX_NOVTABLE CDaoRecordView : public CFormView  
  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoRecordView::CDaoRecordView](../Topic/CDaoRecordView::CDaoRecordView.md)|建構 `CDaoRecordView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoRecordView::IsOnFirstRecord](../Topic/CDaoRecordView::IsOnFirstRecord.md)|如果目前的資料錄是在關聯的資料錄集，之第一筆資料錄傳回非零。|  
|[CDaoRecordView::IsOnLastRecord](../Topic/CDaoRecordView::IsOnLastRecord.md)|如果目前的資料錄是在關聯的資料錄集，的最後一筆資料錄傳回非零。|  
|[CDaoRecordView::OnGetRecordset](../Topic/CDaoRecordView::OnGetRecordset.md)|傳回指向 `CDaoRecordset`從衍生類別的物件。  ClassWizard 覆寫您對這個函式，並視需要建立資料錄集。|  
|[CDaoRecordView::OnMove](../Topic/CDaoRecordView::OnMove.md)|如果目前的資料錄已變更，更新在資料來源中，則移動至指定的資料錄 \(接下來，之前，第一個或前\)。|  
  
## 備註  
 這個檢視是表單檢視直接連接至 `CDaoRecordset` 物件。  這個檢視從對話方塊樣板資源建立並顯示 `CDaoRecordset` 物件的欄位在對話方塊樣板的控制項。  對話資料交換 `CDaoRecordView` 物件使用 \(Dialog Data Exchange，DDX\) 和 DAO 資料錄自動化資料的欄位交換 \(DFX\) 在表單控制項和資料錄集欄位之間的。  `CDaoRecordView` 也提供移動的預設實作移到第一個，下一個，上一個或最後一筆資料錄和用來更新目前的資料錄檢視中。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源，，因為它們使用 Microsoft Jet 資料庫引擎， DAO 類別通常會提供絕佳的功能。  
  
 這是最常見的方式建立資料錄檢視是以應用程式精靈。  為您最基本的起始應用程式的一部分，應用程式精靈建立兩個資料錄檢視類別及其關聯的資料錄集類別。  
  
 如果您需要一個表單，應用程式精靈方法會比較容易。  ClassWizard 在開發程序可讓您決定之後使用資料錄檢視。  如果您沒有以應用程式精靈建立資料錄檢視類別，您可以在稍後建立其與 ClassWizard。  使用 ClassWizard 分別建立資料錄檢視和資料錄集並連接它們是最具彈性的方法，因為它可讓您在命名資料錄集類別的多個控制項和其。H\/.CPP 檔案。  這個方法也可讓您在相同的資料錄集類別的多個資料錄檢視。  
  
 更方便使用者資料錄至資料錄檢視的資料錄，移動到第一個，下一個，上一個或最後一筆資料錄的應用程式精靈建立功能表 \(並選擇性工具列\) 資源中移動。  如果您使用 ClassWizard 資料錄檢視類別，您必須建立這些資源包含功能表的和點陣圖編輯器。  
  
 如需移動的預設實作中的資訊記錄至記錄，請參閱 `IsOnFirstRecord` 和 `IsOnLastRecord` 和文件 [使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)，適用於 `CRecordView` 和 `CDaoRecordView`。  
  
 `CDaoRecordView` 記錄在資料錄集的位置，使得資料錄檢視 \(Record View\) 可以更新使用者介面。  當使用者移至資料錄集內的任一端，此資料錄檢視停用使用者介面物件 \(例如功能表項目或工具列按鈕動作的進一步向相同的方向。  
  
 如需宣告和使用您的資料錄檢視和資料錄集類別的詳細資訊，請參閱\<設計和建立資料錄檢視」本文 [資料錄檢視](../../data/record-views-mfc-data-access.md)上。  如需資料錄檢視如何運作以及如何使用它們的詳細資訊，請參閱本文 [使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  上述的所有文件適用於 `CRecordView` 和 `CDaoRecordView`。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CDaoRecordView`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)