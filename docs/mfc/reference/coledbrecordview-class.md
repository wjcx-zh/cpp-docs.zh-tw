---
title: "COleDBRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDBRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDBRecordView 類別"
  - "MFC, OLE DB"
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDBRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在控制項中顯示資料庫資料錄的檢視。  
  
## 語法  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDBRecordView::COleDBRecordView](../Topic/COleDBRecordView::COleDBRecordView.md)|建構 `COleDBRecordView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDBRecordView::OnGetRowset](../Topic/COleDBRecordView::OnGetRowset.md)|傳回標準 `HRESULT` 值。|  
|[COleDBRecordView::OnMove](../Topic/COleDBRecordView::OnMove.md)|更新目前的資料錄 \(如果已變更\) 在資料來源會移動到指定的資料錄 \(接下來，之前，第一個或前\)。|  
  
## 備註  
 這個檢視是表單檢視直接連接至 `CRowset` 物件。  這個檢視從對話方塊樣板資源建立並顯示 `CRowset` 物件的欄位在對話方塊樣板的控制項。  `COleDBRecordView` 物件使用對話資料交換 \(Dialog Data Exchange，DDX\) 和巡覽功能建置在 `CRowset`， Automation 資料的動作在表單控制項和資料列集欄位之間的。  `COleDBRecordView` 也提供移動的預設實作移到第一個，下一個，上一個或最後一筆資料錄和用來更新目前的資料錄在檢視。  
  
 您可以透過 **COleDbRecordView** 使用 DDX 函式，從資料庫資料錄集直接取得資料並將其顯示於對話方塊控制項中。  您應該透過 **COleDbRecordView** 使用 **DDX\_\*** 方法 \(例如 `DDX_Text`\)，而不是 **DDX\_Field\*** 函式 \(例如 `DDX_FieldText`\)。  `DDX_FieldText` 不適用於 **COleDbRecordView** 一起使用，因為 `DDX_FieldText` 採用型別 **CRecordset\*** \(適用於\) 或 `CRecordView`**CDaoRecordset\*** 的其他引數 \( `CDaoRecordView`\)。  
  
> [!NOTE]
>  如果您使用存取資料時使用物件 \(DAO\) 類別而非 OLE DB 消費者樣板類別，使用類別 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 。  如需詳細資訊，請參閱本文 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 `COleDBRecordView` 記錄使用者在資料列集的位置，使得資料錄檢視 \(Record View\) 可以更新使用者介面。  當使用者移至資料列集時的終止，則資料錄檢視停用使用者介面物件 \(例如功能表項目或工具列按鈕動作的進一步向相同的方向。  
  
 如需資料列集類別的詳細資訊，請參閱 [使用 OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md) 文章。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## 需求  
 **Header:** afxoledb.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)