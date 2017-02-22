---
title: "記錄檢視 (MFC 資料存取) | Microsoft Docs"
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
  - "DAO [C++], 資料錄檢視"
  - "資料庫 [C++], 資料錄檢視"
  - "表單 [C++], 資料存取工作"
  - "MFC [C++], 資料錄檢視"
  - "ODBC 資料錄集 [C++], 資料錄檢視"
  - "資料錄檢視 [C++]"
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 記錄檢視 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節僅適用於 MFC ODBC 和 DAO 類別。  如需 OLE DB 資料錄檢視的詳細資訊，請參閱 [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) 和[使用 OLE DB 資料錄檢視](../data/oledb/using-ole-db-record-views.md)。  
  
 為支援表單架構的資料存取應用程式，類別庫會提供類別 [CRecordView](../mfc/reference/crecordview-class.md) 和類別 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)。  資料錄檢視是表單檢視物件，其控制項直接對應到[資料錄集](../data/odbc/recordset-odbc.md)物件的欄位資料成員 \(並間接對應到資料來源上的查詢結果或資料表中的對應資料行\)。  如同其基底類別 [CFormView](../mfc/reference/cformview-class.md)，`CRecordView` 和 `CDaoRecordView` 也是以對話方塊範本資源為基礎。  
  
## 表單用途  
 表單對於各種資料存取工作非常有用：  
  
-   輸入資料  
  
-   執行資料的唯讀檢查  
  
-   更新資料  
  
## 深入了解資料錄檢視  
 主題中的資料適用於 ODBC 架構和 DAO 架構類別。  若為 ODBC 請使用 `CRecordView`，若為 DAO 則使用 `CDaoRecordView`。  
  
 主題包括：  
  
-   [資料錄檢視類別的功能](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [資料錄檢視的資料交換](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [您在使用資料錄檢視上的角色](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [設計和建立資料錄檢視](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)  
  
## 請參閱  
 [Data Access Programming \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)