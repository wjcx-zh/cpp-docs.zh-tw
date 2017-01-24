---
title: "CRecordView Class | Microsoft Docs"
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
  - "CRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecordView 類別"
  - "ODBC 資料錄集, viewing records"
  - "資料錄, viewing ODBC"
  - "檢視, ODBC"
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在控制項中顯示資料庫資料錄的檢視。  
  
## 語法  
  
```  
class AFX_NOVTABLE CRecordView : public CFormView  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRecordView::CRecordView](../Topic/CRecordView::CRecordView.md)|建構 `CRecordView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRecordView::IsOnFirstRecord](../Topic/CRecordView::IsOnFirstRecord.md)|如果目前的資料錄是在關聯的資料錄集，之第一筆資料錄傳回非零。|  
|[CRecordView::IsOnLastRecord](../Topic/CRecordView::IsOnLastRecord.md)|如果目前的資料錄是在關聯的資料錄集，的最後一筆資料錄傳回非零。|  
|[CRecordView::OnGetRecordset](../Topic/CRecordView::OnGetRecordset.md)|傳回指向 `CRecordset`從衍生類別的物件。  ClassWizard 覆寫您對這個函式，並視需要建立資料錄集。|  
|[CRecordView::OnMove](../Topic/CRecordView::OnMove.md)||  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CRecordView::OnMove](../Topic/CRecordView::OnMove.md)|如果目前的資料錄已變更，更新在資料來源中，則移動至指定的資料錄 \(接下來，之前，第一個或前\)。|  
  
## 備註  
 這個檢視是表單檢視直接連接至 `CRecordset` 物件。  這個檢視從對話方塊樣板資源建立並顯示 `CRecordset` 物件的欄位在對話方塊樣板的控制項。  對話資料交換 `CRecordView` 物件使用 \(Dialog Data Exchange，DDX\) 和 Automation 資料的資料錄欄位交換 \(RFX\) 在表單控制項和資料錄集欄位之間的。  `CRecordView` 也提供移動的預設實作移到第一個，下一個，上一個或最後一筆資料錄和用來更新目前的資料錄在檢視。  
  
> [!NOTE]
>  如果您使用存取資料時使用物件 \(DAO\) 類別而不是開放式資料庫連接 \(ODBC\) 類別會使用類別， [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 。  如需詳細資訊，請參閱本文 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 這是最常見的方式建立資料錄檢視是以應用程式精靈。  為您最基本的起始應用程式的一部分， Tge 應用程式精靈建立兩個資料錄檢視類別及其關聯的資料錄集類別。  如果您沒有以應用程式精靈建立資料錄檢視類別，您可以在稍後建立其與 ClassWizard。  如果您需要一個表單，應用程式精靈方法會比較容易。  ClassWizard 在開發程序可讓您決定之後使用資料錄檢視。  使用 ClassWizard 分別建立資料錄檢視和資料錄集並連接它們是最具彈性的方法，因為它可讓您在命名資料錄集類別的多個控制項和其。H\/.CPP 檔案。  這個方法也可讓您在相同的資料錄集類別的多個資料錄檢視。  
  
 更方便使用者資料錄至資料錄檢視的資料錄，移動到第一個，下一個，上一個或最後一筆資料錄的應用程式精靈建立功能表 \(並選擇性工具列\) 資源中移動。  如果您使用 ClassWizard 資料錄檢視類別，您必須建立這些資源包含功能表的和點陣圖編輯器。  
  
 如需移動的預設實作中的資訊記錄至記錄，請參閱 `IsOnFirstRecord` 和 `IsOnLastRecord` 和本文 [使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
 `CRecordView` 記錄在資料錄集的位置，使得資料錄檢視 \(Record View\) 可以更新使用者介面。  當使用者移至資料錄集內的任一端，此資料錄檢視停用使用者介面物件 \(例如功能表項目或工具列按鈕動作的進一步向相同的方向。  
  
 如需宣告和使用您的資料錄檢視和資料錄集類別的詳細資訊，請參閱\<設計和建立資料錄檢視」本文 [資料錄檢視](../../data/record-views-mfc-data-access.md)上。  如需資料錄檢視如何運作以及如何使用它們的詳細資訊，請參閱本文 [使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)