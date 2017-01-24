---
title: "使用 OLE DB 資料錄檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDBRecordView 類別, 概觀"
  - "MFC, 資料錄檢視"
  - "OLE DB 資料錄檢視"
  - "OLE DB, 資料錄檢視"
  - "資料錄檢視, 資料錄檢視物件"
  - "資料列集, 資料錄檢視"
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 OLE DB 資料錄檢視
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您要在 MFC 應用程式中顯示 OLE DB 資料列集資料，您應該使用 MFC 類別 [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。  從 `COleDBRecordView` 建立的資料錄檢視物件讓您可以在 MFC 控制項顯示資料庫資料錄。  資料錄檢視是一種對話方塊形式檢視，它會直接連接到由 `CRowset` 樣板類別建立的 OLE DB 資料列集物件上。  這種資料列集物件控制代碼的取得方式相當簡單：  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 這個檢視可以顯示對話方塊控制項的 `CRowset` 物件欄位。  `COleDBRecordView` 物件使用對話資料交換 \(Dialog Data Exchange，DDX\) 和建置於 `CRowset` 的 Navigational 功能 \(**MoveFirst**、`MoveNext`、`MovePrev` 和 `MoveLast`\)，以自動化表單上的控制項和資料列集欄位之間的資料移動。  `COleDBRecordView` 會持續追蹤使用者在資料列集的位置，使得資料錄檢視 \(Record View\) 可以更新使用者介面並提供 [OnMove](../Topic/COleDBRecordView::OnMove.md) 方法，在目前的資料錄移動至另一個之前先進行更新。  
  
 您可以透過 **COleDbRecordView** 使用 DDX 函式，從資料庫資料錄集直接取得資料並將其顯示於對話方塊控制項中。  您應該透過 **COleDbRecordView** 使用 **DDX\_\*** 方法 \(例如 `DDX_Text`\)，而不是 **DDX\_Field\*** 函式 \(例如 `DDX_FieldText`\)。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [COleDBRecordView Class](../../mfc/reference/coledbrecordview-class.md)