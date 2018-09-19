---
title: 記錄檢視 （MFC 資料存取） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89677762fd1744afcb6aa749b374dbbb8301d4c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029698"
---
# <a name="record-views--mfc-data-access"></a>記錄檢視 (MFC 資料存取)

本節僅適用於 MFC ODBC 類別。 OLE DB 資料錄檢視的相關資訊，請參閱[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)並[使用 OLE DB 資料錄檢視](../data/oledb/using-ole-db-record-views.md)。  
  
若要支援以 form 為基礎的資料存取應用程式，類別庫會提供類別[CRecordView](../mfc/reference/crecordview-class.md)。 資料錄檢視是表單檢視物件，其控制項直接對應到欄位資料成員[資料錄集](../data/odbc/recordset-odbc.md)物件 （並間接對應的資料行中的查詢結果或資料來源上的資料表）。 如同其基底類別[CFormView](../mfc/reference/cformview-class.md)，`CRecordView`以對話方塊範本資源為基礎。  
  
## <a name="form-uses"></a>表單用途  

表單對於各種資料存取工作非常有用：  
  
- 輸入資料  
  
- 執行資料的唯讀檢查  
  
- 更新資料  
  
## <a name="further-reading-about-record-views"></a>深入了解資料錄檢視  

主題中的資料適用於 ODBC 架構和 DAO 架構類別。 若為 ODBC 請使用 `CRecordView`，若為 DAO 則使用 `CDaoRecordView`。  
  
主題包括：  
  
- [資料錄檢視類別的功能](../data/features-of-record-view-classes-mfc-data-access.md)  
  
- [資料錄檢視的資料交換](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
- [您的角色中使用資料錄檢視](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
- [設計和建立資料錄檢視](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
- [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>另請參閱  

[資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)